---
title: Требования к системе, установка и файлы драйвера | Документы Майкрософт
ms.custom: ''
ms.date: 03/18/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2f451493a93e545fea0507f83fe5195b30ec2680
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "79526809"
---
# <a name="system-requirements-installation-and-driver-files"></a>Системные требования, установка и файлы драйвера

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

В этой статье обсуждаются драйверы ODBC, подключающиеся к SQL Server.

## <a name="sql-version-compatibility"></a>Совместимость с версиями SQL

Совместимость указывает, что драйвер был протестирован на совместимость с существующими выпусками SQL во время выпуска драйвера. Выпуски SQL Server обычно пытаются поддерживать обратную совместимость с существующими драйверами клиента. Но новые функции в выпусках SQL Server могут быть недоступны для более старых версий клиентских драйверов.

|Версия драйвера|База данных SQL Azure|Хранилище SQL|Управляемый экземпляр SQL Azure|SQL Server 2019|SQL Server 2017|SQL Server 2016|SQL Server 2014|SQL Server 2012|SQL Server 2008 R2|SQL Server 2008|SQL Server 2005|
|-|-|-|-|-|-|-|-|-|-|-|-|
|17.5|Да|Да|Да|Да|Да|Да|Да|Да| | | |
|17.4|Да|Да|Да|Да|Да|Да|Да|Да| | | |
|17.3|Да|Да|Да|Да|Да|Да|Да|Да|Да|Да| |
|17.2|Да|Да|Да| |Да|Да|Да|Да|Да|Да| |
|17.1|Да|Да|Да| |Да|Да|Да|Да|Да|Да| |
|17.0|Да|Да|Да| |Да|Да|Да|Да|Да|Да| |
|Версия 13.1| | | | |Да|Да|Да|Да|Да|Да| |
|13  | | | | | |Да|Да|Да|Да|Да| |
|11  | | | | | | |Да|Да|Да|Да|Да|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

### <a name="connection-string-details"></a>Сведения о строке подключения

Имя драйвера, которое следует указывать в строке подключения, — `ODBC Driver 11 for SQL Server` или `ODBC Driver 13 for SQL Server` (как для 13, так и для 13.1) или `ODBC Driver 17 for SQL Server`.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

Следующая таблица указывает на поддержку версии драйвера для версий операционной системы Windows:

|Версия драйвера|Windows Server 2019|Windows Server 2016|Windows Server 2012 R2|Windows Server 2012|Windows Server 2008 R2|Windows 10|Windows 8.1|Windows 7|Windows Vista с пакетом обновления 2 (SP2)|
|-|-|-|-|-|-|-|-|-|-|
|17.5|Да|Да|Да|Да| |Да|Да| | |
|17.4|Да|Да|Да|Да|Да|Да|Да|Да| |
|17.3|Да|Да|Да|Да|Да|Да|Да|Да| |
|17.2| |Да|Да|Да|Да|Да|Да|Да| |
|17.1| |Да|Да|Да|Да|Да|Да|Да| |
|17.0| |Да|Да|Да|Да|Да|Да|Да| |
|Версия 13.1| |Да|Да|Да|Да|Да|Да|Да| |
|13  | | | |Да|Да| |Да|Да| |
|11  | | | |Да|Да| | |Да|Да|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Установка Microsoft ODBC Driver for SQL Server

Драйвер устанавливается при запуске `msodbcsql.msi` из одной из [загрузок для Windows](../download-odbc-driver-for-sql-server.md#download-for-windows).

> [!NOTE]
> Для тех, кто установил драйвер 17.1.0.1 или ниже, рекомендуется удалить его вручную перед установкой новой версии драйвера.

### <a name="side-by-side-with-native-client"></a>Параллельно с Native Client

Драйвер можно установить параллельно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Основные версии драйвера (11, 13, 17) могут быть установлены параллельно друг с другом.

При инициировании `msodbcsql.msi` по умолчанию устанавливаются только клиентские компоненты. Этими компонентами служат файлы, поддерживающие работу приложения, разработанного с помощью драйвера. Чтобы установить компоненты пакета SDK, укажите в командной строке `ADDLOCAL=ALL`. Ниже приведен пример.
  
```console
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  

### <a name="end-user-license"></a>Лицензия пользователя

Укажите `IACCEPTMSODBCSQLLICENSETERMS=YES`, чтобы принять условия лицензионного соглашения, если для установки используется параметр `/passive`, `/qn`, `/qb` или `/qr`. Этот параметр указывается только прописными буквами. Ниже приведен пример.
  
```console
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  

### <a name="silent-uninstall"></a>Удаление без взаимодействия с пользователем

В следующем примере показано выполнение удаления без взаимодействия с пользователем.
  
```console
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  

### <a name="indicate-dependency"></a>Указание зависимость

Если приложение использует драйвер, оно должно указывать, что зависит от драйвера, с помощью параметра установки `APPGUID`. Это позволяет установщику драйвера вывести сведения о зависимых приложениях перед удалением. Чтобы задать зависимость от драйвера, присвойте параметру командной строки `APPGUID` код продукта при автоматической установке драйвера. Код продукта необходимо создать при использовании установщика (Майкрософт) для формирования пакета установки приложения. Ниже приведен пример.
  
```console
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Программы командной строки: sqlcmd.exe и bcp.exe

Программы командной строки `bcp.exe` и `sqlcmd.exe`, которые используются с драйвером, можно загрузить по адресу [Microsoft Command Line Utilities 11 для SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [Microsoft Command Line Utilities 13 для SQL Server](https://www.microsoft.com/download/details.aspx?id=52680) или [Microsoft Command Line Utilities 13.1 для SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). Драйвер является необходимым условием для установки `sqlcmd.exe` и `bcp.exe`.
  
`bcp.exe` и `sqlcmd.exe` устанавливаются во вложенную папку `110\Tools` в `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` для версии 11, и `130\Tools` для 13 и 13.1.

Приложение, использующее функции BCP, должно указывать драйвер из той же версии, которая поставлялась с файлом заголовка и библиотекой, применявшимися при компиляции приложения.  

Например, при компиляции приложения ODBC с помощью `msodbcsql11.lib` и `msodbcsql.h` используйте "DRIVER={ODBC Driver 11 for SQL Server}" в строке подключения.

## <a name="components-of-the-microsoft-odbc-driver-for-ssnoversion-on-windows"></a>Компоненты Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Windows

Драйвер ODBC для Windows состоит из следующих компонентов:

| Компонент | Описание |
| :-------- | :---------- |
|msodbcsql17.dll или <br/> msodbcsql13.dll или <br/> msodbcsql11.dll|Файл библиотеки динамической компоновки (DLL), содержащий все функциональные возможности драйвера. Этот файл устанавливается в папку %SYSTEMROOT%\System32.|  
|msodbcdiag17.dll или <br/> msodbcdiag13.dll или <br/> msodbcdiag11.dll|Файл библиотеки динамической компоновки (DLL), содержащий интерфейс диагностики (трассировка). Этот файл устанавливается в папку %SYSTEMROOT%\System32.|
|msodbcsqlr17.rll или <br/> msodbcsqlr13.rll или <br/> msodbcsqlr11.rll|Сопутствующий файл ресурса для библиотеки драйвера. Этот файл устанавливается в папку %SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm или <br/> s11ch_msodbcsql.chm |Файл справки мастера источников данных, описывающий, как создать источник данных для драйвера. Этот файл устанавливается в папку %SYSTEMROOT%\System32\1033 <br /> <br /> **ПРИМЕЧАНИЕ.** Для драйвера ODBC 17 отсутствует CHM-файл. |  
|msodbcsql.h|Файл заголовка, содержащий все новые определения, необходимые для использования драйвера.<br /><br /> **Примечание.**  В одной программе нельзя сочетать ссылки на msodbcsql.h и odbcss.h.<br /><br /> Файл msodbcsql.h для ODBC Driver 17 или 13 устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> Файл msodbcsql.h для ODBC Driver 11 устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib или <br/> msodbcsql13.lib или <br/> msodbcsql11.lib|Файл библиотеки, необходимый для вызова функций служебной программы **bcp**, являющихся частью драйвера.<br /><br /> **Примечание.**  Если вы включаете в программу ссылку на этот файл библиотеки, убедитесь, что этот файл находится в вашем системном пути, а также в системном пути других пользователей, которые используют это приложение.<br /><br /> Файл msodbcsql17.lib или msodbcsql13.lib устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>См. также раздел

[Драйвер Microsoft ODBC Driver for SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
