# lsx

### ls parts explosion

### Description

List all components of path names.

### Input

Pathnames are given on the command line.

### Output

`ls` produces a long format listing for _every_ component
in every given pathname.

If the option, `--follow` is specified,
then `lsx` also follow _every_ symbolic link,
at every level, until there are none left to resolve,
printing a long form listing for each stage
of symbolic link resolution.

### Why

Sometimes, it can be difficult to know just exactly
where along the path things went wrong.

If you are lucky, all the software you use
comes with `libexplain`.

Failing that, `lsx` might help find the usual suspects.

## Options

--verbose

--debug

--relative

Normally, `lsx` converts to absolute pathnames,
as the first step.  This prevents that from happening.
For all listings, if the given pathname was relative,
then the parts explosion will be relative.

--follow

Resolve all symbolic links,
one by one, from lowest level up.
Print a parts explosion for each stage of symlink resolution.

--header

Print the original pathname as header.
Sometimes parts explosions cat get lengthy,
and if more than one pathname is given,
it can get hard to keep track of which
original path account for which results.

## Example

```
lsx /etc/alternatives/locate
```

## Result
```
drwxr-xr-x 191 root root 12K 2016-06-28 08:54 /etc
drwxr-xr-x   2 root root 20K 2016-06-28 08:54 /etc/alternatives
lrwxrwxrwx   1 root root  16 2015-07-05 14:55 /etc/alternatives/locate -> /usr/bin/mlocate
```

## Example
```
lsx --follow /etc/alternatives/locate
```

## Result

```
drwxr-xr-x 191 root root 12K 2016-06-28 08:54 /etc
drwxr-xr-x   2 root root 20K 2016-06-28 08:54 /etc/alternatives
lrwxrwxrwx   1 root root  16 2015-07-05 14:55 /etc/alternatives/locate -> /usr/bin/mlocate
drwxr-xr-x 11 root root    4.0K 2015-07-14 21:16 /usr
drwxr-xr-x  2 root root    128K 2016-06-28 08:58 /usr/bin
-rwxr-sr-x  1 root mlocate  39K 2014-11-17 23:54 /usr/bin/mlocate

```

## License

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as
published by the Free Software Foundation; either version 3 of the
License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
Lesser General Public License for more details.

You should have received a copy of the GNU Lesser General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

##

-- Guy Shaw

   gshaw@acm.org

