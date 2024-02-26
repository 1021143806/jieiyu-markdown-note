# ��PowerShell ʵս��

## �Ƽ���

PowerShell ���ص�

- һ���Ե���ƣ��﷨��������������
- ����ѧ���ܼ������еĽű�����������й���
- ���÷ḻ�ı�׼���cmd-let������Ĭ�ϻ����¼�����ɳ�����ϵͳ������
- �߱���������չ��ϵ��PowerShellGet�����Ӵ��ģ��ͽű��г���PowerShell Gallery��
- ������ǿ����֧�֡��������� .NET CLR ����֮�ϣ��ܽ��ܲ�����.NET���󡣶����������ڹܵ��ͽ���֮�䴫�ݡ�
- ���µ� PowerShell 7 �ǿ�Դ�Ϳ�ƽ̨�ģ����ƶ��Ĳ�����һ����ҵ�Ĳ�Ʒ����ʮ������ҵ��

## ǰ��

### Ϊʲôʹ�� PowerShell

PowerShell ��Ŀ�������û�ͨ���ű��Զ�ִ����������ѧϰ�������̡�

### Ŀ�����

IT רҵ��ʿ��ϵͳ����Ա��ÿ��ƣ����һ�ɲ����GUI���Ĵ������

### ���ݼ��

ʵ����ѧ�������д���ʾ������ʵ������
������

- ���� PowerShell ����Ҫ���յ�֪ʶ
  - �� 1 ~ 7 �� ������ PowerShell���Ա���
  - �� 8 �� �����������PowerShellԶ�̴���������Զ�̼������ִ������
  - �� 9 �� ==���������µ� PowerShell ���Կ�� Pester==�������ܹᴩ���飬����ʹ�á�

- ���õ�һ������ѧ��֪ʶ���Զ�ִ��һЩ����������
  - �� 10 ~ 13 �� ��������ν����ṹ�����ݣ��Լ��ܶ�IT����Ա����ʹ�õķ���
  - �� 14 �� չʾ����ι������ߣ��Ա����Լ��Ļ�������������
- �ص㹹������Ϊ PowerLab �� PowerShell ģ�飬�����ʾ�� PowerShell �Ĺ��ܡ��ⲿ�ֺ��������ģ����Ʒ�ʽ�Լ��뺯����ص����ʵ����
  - �� 15 ~ 20 �� ���������ʹ�� PowerShell ʵ������ʵ���ҵ��Զ������Լ�����Զ����Է�����������

## ��һ���� ����֪ʶ

### �� 1 �� ��������

#### 1.1 �� PowerShell ����̨

#### 1.2 ʹ�� DOS ����

����|ע��
:---:|:----:
TAB | ������
cd | ����Ŀ¼
dir | ��ʾ��ǰĿ¼����
cls | �����Ļ

#### 1.3 ̽�� PowerShell ����

�������

1. cmdlet
2. ����
3. ����
4. �ⲿ�ű�

Get-Command ����

``` powershell
PS C:\Users\375563> get-command -name get-alias

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Alias                                          3.1.0.0    Microsoft.PowerShell.Utility
```

#### 1.4 ��ȡ����

##### 1.4.1 ��ʾ�ĵ�

``` powershell
PS C:\Users\375563> get-help add-content

����
    Add-Content

ժҪ
    Adds content to the specified items, such as adding words to a file.


�﷨
    Add-Content [-Value] <System.Object[]> [-Credential <System.Management.Automation.PSCredential>] [-Encoding {AS
    CII | BigEndianUnicode | BigEndianUTF32 | Byte | Default | OEM | String | Unicode | Unknown | UTF7 | UTF8 | UTF
    32}] [-Exclude <System.String[]>] [-Filter <System.String>] [-Force] [-Include <System.String[]>] -LiteralPath
    <System.String[]> [-NoNewline] [-PassThru] [-Stream <System.String>] [-UseTransaction] [-Confirm] [-WhatIf] [<C
    ommonParameters>]

    Add-Content [-Path] <System.String[]> [-Value] <System.Object[]> [-Credential <System.Management.Automation.PSC
    redential>] [-Encoding {ASCII | BigEndianUnicode | BigEndianUTF32 | Byte | Default | OEM | String | Unicode | U
    nknown | UTF7 | UTF8 | UTF32}] [-Exclude <System.String[]>] [-Filter <System.String>] [-Force] [-Include <Syste
    m.String[]>] [-NoNewline] [-PassThru] [-Stream <System.String>] [-UseTransaction] [-Confirm] [-WhatIf] [<Common
    Parameters>]


˵��
    The `Add-Content` cmdlet appends content to a specified item or file. Content can be passed in from the pipelin
    e or specified by using the Value parameter.

    If you need to create files or directories for the following examples, see New-Item (New-Item.md).

```

##### 1.4.2 ѧϰһ������

#### 1.5 �����ĵ�

update-help

### �� 2 �� PowerShell ��������

��һ�нԶ���

#### 2.1 ����

�������ڴ洢ֵ

##### 2.1.1 ��ʾ���޸ı���

�����ԣ�$����ͷ
��ʾ����ֵ

``` powershell
PS C:\Users\375563> $MaximumHistoryCount
4096
```

$MaximumHistoryCount ��һ�����ñ�����ָ���� PowerShell ��������ʷ�����洢���ٸ����Ĭ��Ϊ4096����

�޸ı�����ֵ

``` powershell
PS C:\Users\375563> $MaximumHistoryCount = 200
PS C:\Users\375563> $MaximumHistoryCount
200
```

�� PowerShell �б�����Ϊ�����ࣺ

1. �û�����ı���
2. �Զ��������� PowerShell �Դ��ı���

##### 2.1.2 �û�����ı���

###### �����ϸ�ģʽ

```powershell
set-strictmode -version latest
```

�ϸ�ģʽ�£�����Υ�����õı��ʵ����PowerShell ���׳�����һ�㲻����
����

```powershell
get-help set-strictmode -examples
```

��������

```powershell
#color = 'bulu'
```

�� Set-Variable �����һ������
�� Get-Variavle ������ʾ�ñ�����ֵ

```powershell
PS C:\Users\375563> Set-Variable -name color1 -value bule1
PS C:\Users\375563> get-Variable -name color1

Name                           Value
----                           -----
color1                         bule1
```

Set-Variable �����Է������п��ñ���

##### 2.1.3 �Զ�����

###### $null ����

�����ֵ

�����嵥2-8 Ϊ������ֵ$null

```shell
PS C:\WINDOWS\system32> $foo = $null
PS C:\WINDOWS\system32> $foo
PS C:\WINDOWS\system32> $bar
��������������$bar������Ϊδ���øñ�����
����λ�� ��:1 �ַ�: 1
+ $bar
+ 
    + CategoryInfo          : InvalidOperation: (bar:String) []��RuntimeException
    + FullyQualifiedErrorId : VariableIsUndefined
```

�����嵥2-9 ��Get-Variable������ұ���

```shell
PS C:\WINDOWS\system32> get-variable -name foo

Name                           Value
----                           -----
foo


PS C:\WINDOWS\system32> get-variable -name bar
get-variable : �Ҳ�����Ϊ��bar���ı�����
����λ�� ��:1 �ַ�: 1
+ get-variable -name bar
+ ~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (bar:String) [Get-Variable], ItemNotFoundException
    + FullyQualifiedErrorId : VariableNotFound,Microsoft.PowerShell.Commands.GetVariableCommand
```

$null �ǳ�����

###### $LASTEXITCODE ����

�������н�����᷵��һ��**�˳���**������������룩һ�� 0 ��ʾ�ɹ���
$LASTEXITCODE ������ֵʼ�������ִ���Ǹ�������˳��롣

```shell
PS C:\WINDOWS\system32> ping.exe -n 1 dfdfdf.com

���� Ping hdr-nlb5-4e815dd67a14bf7f.elb.us-east-2.amazonaws.com [3.130.253.23] ���� 32 �ֽڵ�����:
����ʱ��

3.130.253.23 �� Ping ͳ����Ϣ:
    ���ݰ�: �ѷ��� = 1���ѽ��� = 0����ʧ = 1 (100% ��ʧ)��
PS C:\WINDOWS\system32> ping.exe -n 1 10.68.2.31

���� Ping 10.68.2.31 ���� 32 �ֽڵ�����:
���� 10.68.2.31 �Ļظ�: �ֽ�=32 ʱ��=6ms TTL=62

10.68.2.31 �� Ping ͳ����Ϣ:
    ���ݰ�: �ѷ��� = 1���ѽ��� = 1����ʧ = 0 (0% ��ʧ)��
�����г̵Ĺ���ʱ��(�Ժ���Ϊ��λ):
    ��� = 6ms��� = 6ms��ƽ�� = 6ms
```

###### ƫ�����ñ���

����������ڿ��Ƹ����������Ĭ����Ϊ
����Error�� Warning��Verbose��Debug��Information

#### 2.2 ��������

PowerShell �ж����������ͣ���������ֵ���ַ����������������޸ı������������Ͳ��ᱨ��

```shell
PS C:\Users\375563> $foo =1
PS C:\Users\375563> $foo = 'one'
PS C:\Users\375563> $foo = $true
```

##### 2.2.1 ����ֵ

�� PowerShell �У�����ֵ���� bools���ֱ�ʹ�� $true �� $false ��ʾ

```shell
PS C:\Users\375563> $isOn = $true
PS C:\Users\375563> $isOn
True
```

##### 2.2.2 �����͸�����

- ��������
  - С�����ֻ���������
  - ��������
  - Int32 (-2147483648,2147483647)
  - Int64 (-9223372036854775808,9223372036854775807)

```shell
  PS K:\vscode\jieiyu-markdown-note> $num = 1
PS K:\vscode\jieiyu-markdown-note> $num    
1
PS K:\vscode\jieiyu-markdown-note> $num.GetType().name
Int32
PS K:\vscode\jieiyu-markdown-note> $num = 1.5
PS K:\vscode\jieiyu-markdown-note> $num.GetType().name
Double
PS K:\vscode\jieiyu-markdown-note> [Int32]$num
2
```

- ��������������
  - Double

##### 2.2.3 �ַ���

- �ϲ��ַ����ͱ���

```shell
PS K:\vscode\jieiyu-markdown-note> $language = 'PowerShell'
PS K:\vscode\jieiyu-markdown-note> $color = 'blue'
PS K:\vscode\jieiyu-markdown-note> $sentence = "Today $color" 
PS K:\vscode\jieiyu-markdown-note> $sentence
Today blue
PS K:\vscode\jieiyu-markdown-note> $color = 'blue2'
PS K:\vscode\jieiyu-markdown-note> $sentence
Today blue
PS K:\vscode\jieiyu-markdown-note> $sentence = "Today $color"
PS K:\vscode\jieiyu-markdown-note> $sentence
Today blue2
```

- ��������˫����

#### 2.3 ����

һ�нԶ���
������ĳ��ģ��ĵ���ʵ�������ģ���Ϊ�ָ࣬���˶�������Ķ�����
��Ŷ��Ŷ�������������������Щ�������á�

##### 2.3.1 �鿴����

```shell
PS K:\vscode\jieiyu-markdown-note> $color = 'red'
PS K:\vscode\jieiyu-markdown-note> $color
red
PS K:\vscode\jieiyu-markdown-note> Select-Object -InputObject $color -Property *

Length
------
     3


PS K:\vscode\jieiyu-markdown-note> $color.Length
3'
```

##### 2.3.2 ʹ�� Get-Member cmdlet

```shell
PS K:\vscode\jieiyu-markdown-note> Get-Member -InputObject $color


   TypeName:System.String

Name             MemberType            Definition
----             ----------            ----------
Clone            Method                System.Object Clone(), System.Object ICloneable.Clone()
CompareTo        Method                int CompareTo(System.Object value), int CompareTo(string strB), int IComparable.CompareTo(System.Object obj), int IComparable[string].CompareTo(string other)
Contains         Method                bool Contains(string value)
CopyTo           Method                void CopyTo(int sourceIndex, char[] destination, int destinationIndex, int count)
EndsWith         Method                bool EndsWith(string value), bool EndsWith(string value, System.StringComparison comparisonType), bool EndsWith(string value, bool ignoreCase, cultureinfo culture)
Equals           Method                bool Equals(System.Object obj), bool Equals(string value), bool Equals(string value, System.StringComparison comparisonType), bool IEquatable[string].Equals(string other)
GetEnumerator    Method                System.CharEnumerator GetEnumerator(), System.Collections.IEnumerator IEnumerable.GetEnumerator(), System.Collections.Generic.IEnumerator[char] IEnumerable[char].GetEnumerator()        
GetHashCode      Method                int GetHashCode()
GetType          Method                type GetType()
GetTypeCode      Method                System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
IndexOf          Method                int IndexOf(char value), int IndexOf(char value, int startIndex), int IndexOf(string value), int IndexOf(string value, int startIndex), int IndexOf(string value, int startIndex, int ... 
IndexOfAny       Method                int IndexOfAny(char[] anyOf), int IndexOfAny(char[] anyOf, int startIndex), int IndexOfAny(char[] anyOf, int startIndex, int count)
Insert           Method                string Insert(int startIndex, string value)
IsNormalized     Method                bool IsNormalized(), bool IsNormalized(System.Text.NormalizationForm normalizationForm)
LastIndexOf      Method                int LastIndexOf(char value), int LastIndexOf(char value, int startIndex), int LastIndexOf(string value), int LastIndexOf(string value, int startIndex), int LastIndexOf(string value, ... 
LastIndexOfAny   Method                int LastIndexOfAny(char[] anyOf), int LastIndexOfAny(char[] anyOf, int startIndex), int LastIndexOfAny(char[] anyOf, int startIndex, int count)
Normalize        Method                string Normalize(), string Normalize(System.Text.NormalizationForm normalizationForm)
PadLeft          Method                string PadLeft(int totalWidth), string PadLeft(int totalWidth, char paddingChar)
PadRight         Method                string PadRight(int totalWidth), string PadRight(int totalWidth, char paddingChar)
Remove           Method                string Remove(int startIndex, int count), string Remove(int startIndex)
Replace          Method                string Replace(char oldChar, char newChar), string Replace(string oldValue, string newValue)
Split            Method                string[] Split(Params char[] separator), string[] Split(char[] separator, int count), string[] Split(char[] separator, System.StringSplitOptions options), string[] Split(char[] separ...
StartsWith       Method                bool StartsWith(string value), bool StartsWith(string value, System.StringComparison comparisonType), bool StartsWith(string value, bool ignoreCase, cultureinfo culture)
Substring        Method                string Substring(int startIndex), string Substring(int startIndex, int length)
ToBoolean        Method                bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte           Method                byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar           Method                char IConvertible.ToChar(System.IFormatProvider provider)
ToCharArray      Method                char[] ToCharArray(), char[] ToCharArray(int startIndex, int length)
ToDateTime       Method                datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal        Method                decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble         Method                double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16          Method                int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32          Method                int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64          Method                long IConvertible.ToInt64(System.IFormatProvider provider)
ToLower          Method                string ToLower(), string ToLower(cultureinfo culture)
ToLowerInvariant Method                string ToLowerInvariant()
ToSByte          Method                sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle         Method                float IConvertible.ToSingle(System.IFormatProvider provider)
ToString         Method                string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.ToString(System.IFormatProvider provider)
ToType           Method                System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16         Method                uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32         Method                uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64         Method                uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
ToUpper          Method                string ToUpper(), string ToUpper(cultureinfo culture)
ToUpperInvariant Method                string ToUpperInvariant()
Trim             Method                string Trim(Params char[] trimChars), string Trim()
TrimEnd          Method                string TrimEnd(Params char[] trimChars)
TrimStart        Method                string TrimStart(Params char[] trimChars)
Chars            ParameterizedProperty char Chars(int index) {get;}
Length           Property              int Length {get;}
```

##### 2.3.3 ���÷���

�鿴�ַ����� Remobe() ����

```shell
   TypeName:System.String

Name   MemberType Definition
----   ---------- ----------
Remove Method     string Remove(int startIndex, int count), string Remove(int startIndex)
```

���÷���

```shell
PS K:\vscode\jieiyu-markdown-note> $color.Remove(1,1)
rd
PS K:\vscode\jieiyu-markdown-note> $color            
red
```

#### 2.4 ���ݽṹ

���ݽṹ

```mermaid
graph LR
A(���ݽṹ) --> 1.����
A --> 2.Array-List
A --> 3.��ϣ��
```

##### 2.4.1 ����

###### ��������

```shell
PS K:\vscode\jieiyu-markdown-note> $colorPicker = @('blue','white','yellow','black')
PS K:\vscode\jieiyu-markdown-note> $colorPicker
blue
white
yellow
black
```

###### ��ȡ����Ԫ��

```shell
PS K:\vscode\jieiyu-markdown-note> $colorPicker[0]
blue
```

���ʶ��Ԫ��

```shell
PS K:\vscode\jieiyu-markdown-note> 1..3           
1
2
3
PS K:\vscode\jieiyu-markdown-note> $colorPicker[1..3]
white
yellow
black
```

###### ��Ԫ����ӵ�����

```shell
PS K:\vscode\jieiyu-markdown-note> $colorPicker = $colorPicker + ��orange'
PS K:\vscode\jieiyu-markdown-note> $colorPicker
blue
white
yellow
black
orange
```

ʹ�� +=

```shell
PS K:\vscode\jieiyu-markdown-note> $colorPicker += ��brown'
PS K:\vscode\jieiyu-markdown-note> $colorPicker
blue
white
yellow
black
orange
brown
```

##### 2.4.2 ArrayList

ArrayList �Ĵ�С����ӻ�ɾ��Ԫ�غ�ɶ�̬�����������������ʱ����ʮ����Խ��

���� ArrayList

```shell
PS K:\vscode\jieiyu-markdown-note> $colorPicker = [System.Collections.ArrayList]@('blue','white','yellow','black')
PS K:\vscode\jieiyu-markdown-note> $colorPicker
blue
white
yellow
black
```

###### ��Ԫ����ӵ�ArrayList

```shell
PS K:\vscode\jieiyu-markdown-note> $colorPicker.Add('gray')
4
PS K:\vscode\jieiyu-markdown-note> $null = $colorPicker.Add('gray')  //��ֹ���
PS K:\vscode\jieiyu-markdown-note> $colorPicker
blue
white
yellow
black
gray
gray
```

###### ArrayList ��ɾ��Ԫ��

```shell
PS K:\vscode\jieiyu-markdown-note> $null = $colorPicker.Remove('gray') 
PS K:\vscode\jieiyu-markdown-note> $colorPicker
blue
white
yellow
black
gray
```

����ͨ��ֵ����������Ԫ�أ�����ж����ͬ����ɾ���뿪ͷ�����Ԫ�ء�

##### 2.4.3 ��ϣ��

�������ݶ�Ӧ������ϣ���ֵ䣩
���-ֵ��
