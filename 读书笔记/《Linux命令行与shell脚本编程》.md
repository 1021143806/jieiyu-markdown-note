# Linux��������shell�ű����

## ��һ���� Linux������

### ��1�� ����Linux shell

### ��2�� �߽�shell

### ��3�� bash shell��������

## �ڶ����� shell�ű���̻���

### ��14�� �����û�����

#### 14.1���ݲ���

``` Shell
./addem 10 30
```

##### 14.1.1��ȡ����

λ�ò�����positional parameter��

|$0|�ű���|
|-|-|
|$1|��һ�������в���|
|$2|�ڶ��������в���|
|$3|�����������в���|
|$4|���ĸ������в���|
|$5|����������в���|
|...|...|

```Shell
$ cat positional1.sh
#!/bin/bash
# Using one command-line parameter ����׳�
#
factorial=1
for (( number = 1; number <= $1; number++ ))
do
factorial=$[ $factorial * $number ]
done
echo The factorial of $1 is $factorial
exit
$
$ ./positional1.sh 5
The factorial of 5 is 120  
$
����֮���ÿո�ָ�
```

```Shell
$ cat positional10.sh
#!/bin/bash
# Handling lots of command-line parameters
#
product=$[ ${10} * ${11} ]
echo The tenth parameter is ${10}.
echo The eleventh parameter is ${11}.
echo The product value is $product.
exit
$
$ ./positional10.sh 1 2 3 4 5 6 7 8 9 10 11 12
The tenth parameter is 10.
The eleventh parameter is 11.
The product value is 110.
$
```

##### 14.1.2��ȡ�ű���

```Shell
$ cat positional0.sh
#!/bin/bash
# Handling the $0 command-line parameter
#
echo This script name is $0.
exit
$
$ bash positional0.sh
This script name is positional0.sh.
$
```

basename���Է��ز�����·���Ľű���

```Shell
$ cat posbasename.sh
#!/bin/bash
# Using basename with the $0 command-line parameter
#
name=$(basename $0)
#
echo This script name is $name.
exit
$
$ ./posbasename.sh
This script name is posbasename.sh.
$
```

```Shell
$ cat checksystem.sh
#!/bin/bash
# Using the $0 command-line parameter in messages
#
scriptname=$(basename $0)
#
echo The $scriptname ran at $(date) >> $HOME/scripttrack.log
exit
$
$ ./checksystem.sh
$ cat $HOME/scripttrack.log
The checksystem.sh ran at Thu 04 Jun 2020 10:01:53 AM EDT
$
```

##### 14.1.3��������

������нű�ʱû��ָ������Ĳ���������ܳ�����

#### 14.2�����������

##### 14.2.1����ͳ��

 $#

 !($#)

?

|�������|����|
|-|-|
|$#|�ű�����ʱЯ���������в����ĸ���
û���κβ���ʱ��$#��ֵΪ0|
|!{$#}|���һ��λ�ñ���
û���κβ���ʱ�����ؽű���|

```Shell
$ cat countparameters.sh
#!/bin/bash
# Counting command-line parameters
#
if [ $# -eq 1 ]
then
fragment="parameter was"
else
fragment="parameters were"
fi
echo $# $fragment supplied.
exit
$
$ ./countparameters.sh
0 parameters were supplied.
$
$ ./countparameters.sh Hello
1 parameter was supplied.
$
$ ./countparameters.sh Hello World
2 parameters were supplied.
$
$ ./countparameters.sh "Hello World"
1 parameter was supplied.
$
```

##### 14.2.2��ȡ��������

|�������|����|
|-|-|
|$*|��������Ϊ����|
|$@|��������Ϊ��������ĵ���|

?

?

```Shell
$ cat grabbingallparams.sh
#!/bin/bash
# Testing different methods for grabbing all the parameters
#
echo
echo "Using the \$* method: $*"
echo
exit
$
$ ./grabbingallparams.sh alpha beta charlie delta

Using the $* method: alpha beta charlie delta

$
```

```Shell
$ cat grabdisplayallparams.sh
#!/bin/bash
# Exploring different methods for grabbing all the parameters
#
echo
echo "Using the \$* method: $*"
count=1
for param in "$*"
do
echo "\$* Parameter #$count = $param"
count=$[ $count + 1 ]
done
echo
exit
$
$ ./grabdisplayallparams.sh alpha beta charlie delta

Using the $* method: alpha beta charlie delta
$* Parameter #1 = alpha beta charlie delta
$
```

?

```Shell
$ cat grabbingallparams.sh
#!/bin/bash
# Testing different methods for grabbing all the parameters
#
echo
echo "Using the \$@ method: $@"
echo
exit
$
$ ./grabbingallparams.sh alpha beta charlie delta

Using the $@ method: alpha beta charlie delta

$
```

```Shell
$ cat grabdisplayallparams.sh
#!/bin/bash
# Exploring different methods for grabbing all the parameters
#
echo
echo "Using the \$@ method: $@"
count=1
for param in "$@"
do
echo "\$@ Parameter #$count = $param"
count=$[ $count + 1 ]
done
echo
exit
$
$ ./grabdisplayallparams.sh alpha beta charlie delta

Using the $@ method: alpha beta charlie delta
$@ Parameter #1 = alpha
$@ Parameter #2 = beta
$@ Parameter #3 = charlie
$@ Parameter #4 = delta

$
```

?

#### 14.3�ƶ�����

##### shift ת�� / �ı� / �ְ�

```Shell
$ cat shiftparams.sh
#!/bin/bash
# Shifting through the parameters
#
echo
echo "Using the shift method:"
count=1
while [ -n "$1" ]
do
echo "Parameter #$count = $1"
count=$[ $count + 1 ]
shift
done
echo
exit
$
$ ./shiftparams.sh alpha bravo charlie delta

Using the shift method:
Parameter #1 = alpha
Parameter #2 = bravo
Parameter #3 = charlie
Parameter #4 = delta

$
```

##### ����

n����ѡ�������ڵ���1��С�ڵ��ڲ���������������Ĭ��Ϊ1��

#### 14.4����ѡ��

ͬʱ�ṩ������ѡ���bash����

##### 14.4.1����ѡ��

###### 1.�����ѡ��

```Shell
$ cat extractoptions.sh
#!/bin/bash
# Extract command-line options
#
echo
while [ -n "$1" ]
do
case "$1" in
-a) echo "Found the -a option" ;;
-b) echo "Found the -b option" ;;
-c) echo "Found the -c option" ;;
*) echo "$1 is not an option" ;;
esac
shift
done
echo
exit
$
$ ./extractoptions.sh -a -b -c -d

Found the -a option
Found the -b option
Found the -c option
-d is not an option

$
```

case������ÿ��������ȷ���Ƿ�Ϊ��Ч��ѡ��ҵ�һ������һ��

###### 2.���������ѡ��

˫���ַ���--��

?

?

```Shell
$ cat extractoptionsparams.sh
#!/bin/bash
# Extract command-line options and parameters
#
echo
while [ -n "$1" ]
do
case "$1" in
-a) echo "Found the -a option" ;;
-b) echo "Found the -b option" ;;
-c) echo "Found the -c option" ;;
--) shift
break;;           #break����whileѭ������Ҫ�ټ���һ��shift
*) echo "$1 is not an option" ;;
esac
shift
done
#
echo
count=1
for param in $@
do
echo "Parameter #$count: $param"
count=$[ $count + 1 ]
done
echo
exit
$
```

?

```Shell
$ ./extractoptionsparams.sh -a -b -c test1 test2 test3

Found the -a option
Found the -b option
Found the -c option
test1 is not an option
test2 is not an option
test3 is not an option

$
```

```Shell
$ ./extractoptionsparams.sh -a -b -c -- test1 test2 test3

Found the -a option
Found the -b option
Found the -c option

Parameter #1: test1
Parameter #2: test2
Parameter #3: test3

$
```

###### 3.����ֵ��ѡ��

```Shell
$ cat extractoptionsvalues.sh
#!/bin/bash
# Extract command-line options and values
#
echo
while [ -n "$1" ]
do
case "$1" in
-a) echo "Found the -a option" ;;
-b) param=$2
echo "Found the -b option with parameter value $param"
shift;;
-c) echo "Found the -c option" ;;
--) shift
break;;
*) echo "$1 is not an option" ;;
esac
shift
done
#
echo
count=1
for param in $@
do
echo "Parameter #$count: $param"
count=$[ $count + 1 ]
done
exit
$
$ ./extractoptionsvalues.sh -a -b BValue -d

Found the -a option
Found the -b option with parameter value BValue
-d is not an option
$
```

##### 14.4.2ʹ��getopt���-ab����)

###### 1.�����ʽ

getopt optstring parameters

��optstring���г�Ҫ�ڽű����õ���ÿ��������ѡ����ĸ��Ȼ����ÿ����Ҫ����ֵ��ѡ����ĸ�����һ��ð�š�

ab:cd������Ϊabcd������b��Ҫ�������ֵ

```Shell
$ getopt ab:cd -a -b BValue -cd test1 test2
-a -b BValue -c -d -- test1 test2
$
```

���棺getopt��getopts�����߼��İ汾������������

###### 2.�ڽű���ʹ��getopt

set -- $(getopt -q ab:cd "$@")

```Shell
$ cat extractwithgetopt.sh
#!/bin/bash
# Extract command-line options and values with getopt
#���Խ�λ�ñ�����ֵ�滻��set������ָ����ֵ��
set -- $(getopt -q ab:cd "$@")
#
echo
while [ -n "$1" ]
do
case "$1" in
-a) echo "Found the -a option" ;;
-b) param=$2
echo "Found the -b option with parameter value $param"
shift;;
-c) echo "Found the -c option" ;;
--) shift
break;;
*) echo "$1 is not an option" ;;
esac
shift
done
#
echo
count=1
for param in $@
do
echo "Parameter #$count: $param"
count=$[ $count + 1 ]
done
exit
$
```

getopt����ó�������ո�������Ĳ���ֵ  ��test1 test2"

##### 14.4.3 ??ʹ��getopts����

```Shell
$ cat extractwithgetopts.sh
#!/bin/bash
# Extract command-line options and values with getopts
#
echo
while getopts :ab:c opt
do
case "$opt" in
a) echo "Found the -a option" ;;
b) echo "Found the -b option with parameter value $OPTARG";;
c) echo "Found the -c option" ;;
*) echo "Unknown option: $opt" ;;
esac
done
exit
$
$ ./extractwithgetopts.sh -ab BValue -c

Found the -a option
Found the -b option with parameter value BValue
Found the -c option
$
```

#### 14.5ѡ���׼��

ͨ��

- case����в������ַ�--

- �����ڲ���ֵ�м���ո�

```Shell
$ ./extractwithgetopts.sh -b "BValue1 BValue2" -a

Found the -b option with parameter value BValue1 BValue2
Found the -a option
$
```

- ���Խ�ѡ����ĸ�Ͳ���ֵд��һ������֮�䲻�ӿո�

```Shell
$ ./extractwithgetopts.sh -abBValue

Found the -a option
Found the -b option with parameter value BValue
$
```

- �ܹ���-bѡ������ȷ������ֵ,���ҿ��Խ�δ�����ѡ�����Ϊ'?'

```Shell
$ ./extractwithgetopts.sh -d

Unknown option: ?
$
$ ./extractwithgetopts.sh -ade

Found the -a option
Unknown option: ?
Unknown option: ?
$
```

�ڴ���ÿ��ѡ��ʱ��getopts�ὫOPTIND��������ֵ��1������ʹ��shift��OPTINDֵ���ƶ�����

##### OPTIND

```Shell
$ cat extractoptsparamswithgetopts.sh
#!/bin/bash
# Extract command-line options and parameters with getopts
#
echo
while getopts :ab:cd opt
do
case "$opt" in
a) echo "Found the -a option" ;;
b) echo "Found the -b option with parameter value $OPTARG";;
c) echo "Found the -c option" ;;
d) echo "Found the -d option" ;;
*) echo "Unknown option: $opt" ;;
esac
done
#
shift $[ $OPTIND - 1 ]
#
echo
count=1
for param in "$@"
do
echo "Parameter $count: $param"
count=$[ $count + 1 ]
done
exit
$
$ ./extractoptsparamswithgetopts.sh -db BValue test1 test2

Found the -d option
Found the -b option with parameter value BValue

Parameter 1: test1
Parameter 2: test2
$/h5
```

?

|ѡ��|����|
|-|-|
|-a|��ʾ���ж���|
|-c|���ɼ���|
|-d|ָ��Ŀ¼|
|-e|��չ����|
|-f|ָ���������ݵ��ļ�|
|-h|��ʾ����İ�����Ϣ|
|-i|�����ı���Сд|
|-l|��������ʽ���|
|-n|ʹ�÷ǽ���ģʽ��������|
|-o|����������ض�����ָ�����ļ�|
|-q|�Ծ�Ĭģʽ����|
|-r|�ݹ鴦��Ŀ¼���ļ�|
|-s|�Ծ�Ĭģʽ����|
|-v|������ϸ���|
|-x|�ų�ĳ������|
|-y|����������ش�yes|

#### 14.6 ��ȡ�û�����

����Ľ���������ʱѯ���û����ȴ��û��ش�

##### 14.6.1 �����Ķ�ȡ

```Shell
$ cat askname.sh
#!/bin/bash
# Using the read command
#
echo -n "Enter your name: "
read name
echo "Hello $name, welcome to my script."
exit
$
$ ./askname.sh
Enter your name: Richard Blum
Hello Richard Blum, welcome to my script.
$
```

## �������� �߼�shell�ű����

## ���Ĳ��� ����ʵ�ýű�
