---
title: Creating a directory
description: Creating a directory in PHP
sidebar:
  label: Create a directory
---

## Create a directory: `mkdir()`
If you need to create a directory, you can use the `mkdir()` function.

The `mkdir()` function has one mandatory parameter, the name of the directory you want to create:

```php
$return = mkdir("./testdir");
var_dump($return);
```

The function returns a boolean value, the `true` value if the directory is created, otherwise it returns `false` value.

For example if the directory already exists, it returns `false`.

### Permissions

You can also define permissions.

For example, if you want to create a directory with read, write and execute permission for the **u**ser, the **g**roup, and the **o**thers you can use the `0777` value:

```php
$return = mkdir("./testdir", 0777);
var_dump($return);
```

If you notice that the directory created has no right permission my suggestion is to check if you have some `umask` configuration.

For example, a workaround is to unset the `umask` in order to avoid that it interferes with permissions:

```php
$old = umask(0);
$return = mkdir("./testdir", 0777);
var_dump($return);
umask($old);
```

### Nested directories

If you want to create nested directories (like `mkdir -p` in the shell environment), you can use the third parameter, a `boolean` parameter that indicates that you want nested directory:

```php
$return = mkdir("./testdir/testdir1/testdir2/testdir3", 0777, true);
var_dump($return);
umask($old);
```