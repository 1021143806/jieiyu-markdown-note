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

�����ϸ�ģʽ

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
