---
title: Требования к системе, установка и файлы драйвера | Документы Майкрософт
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76016e87767f4efbca9a6c845af6464ab3ca26ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989398"
---
# <a name="system-requirements-installation-and-driver-files"></a>Системные требования, установка и файлы драйвера
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает подключения к SQL Server 2014, SQL Server 2012, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)] и [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Windows можно установить на компьютере, где также имеется одна или несколько версий Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
Драйвер ODBC 13 и 13,1 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в дополнение к описанной выше, поддерживает SQL Server 2016. 

Драйвер ODBC 17 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает все перечисленные выше версии, а также SQL Server 2017.

Драйвер ODBC 17 для SQL Server поддерживает SQL Server 2019 начиная с версии драйвера 17,3.

Имя драйвера, указанное в строке подключения, равно `ODBC Driver 11 for SQL Server` или `ODBC Driver 13 for SQL Server` (для 13 и 13,1) или `ODBC Driver 17 for SQL Server`.
  
## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы

Запускать приложения с помощью драйвера можно в следующих операционных системах Windows:  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(только ODBC Driver 11)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Установка Microsoft ODBC Driver for SQL Server

Драйвер устанавливается при запуске `msodbcsql.msi` по одной из следующих ссылок:

- [Скачать Microsoft ODBC Driver 17 for SQL Server для Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Скачать Microsoft ODBC Driver 13.1 for SQL Server для Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Скачать Microsoft ODBC Driver 13 for SQL Server для Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Скачать Microsoft ODBC Driver 11 for SQL Server для Windows](https://www.microsoft.com/download/details.aspx?id=36434). 

> [!NOTE]
> Для тех, кто установил драйвер 17.1.0.1 или ниже, рекомендуется удалить его вручную перед установкой новой версии драйвера.

Его можно установить параллельно с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  

При инициировании `msodbcsql.msi` по умолчанию устанавливаются только клиентские компоненты. Этими компонентами служат файлы, поддерживающие работу приложения, разработанного с помощью драйвера. Чтобы установить компоненты пакета SDK, укажите в командной строке `ADDLOCAL=ALL`. Пример:  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 Укажите `IACCEPTMSODBCSQLLICENSETERMS=YES`, чтобы принять условия лицензионного соглашения, если для установки используется параметр `/passive`, `/qn`, `/qb` или `/qr`. Этот параметр указывается только прописными буквами. Пример:  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 Для выполнения автоматического удаления  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
Если приложение использует драйвер, оно должно указывать, что зависит от драйвера, с помощью параметра установки `APPGUID`. Это позволяет установщику драйвера вывести сведения о зависимых приложениях перед удалением. Чтобы задать зависимость от драйвера, присвойте параметру командной строки `APPGUID` код продукта при автоматической установке драйвера. (Код продукта необходимо создать при использовании установщика Майкрософт для формирования пакета установки приложения.) Пример:  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Программы командной строки: sqlcmd.exe и bcp.exe

Средства `bcp.exe` и`sqlcmd.exe` для использования с драйвером можно загрузить на сайте [Microsoft программы командной строки 11 для SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [Microsoft программы командной строки 13 для SQL Server](https://www.microsoft.com/download/details.aspx?id=52680)или [Microsoft программы командной строки 13,1 для SQL Server](https://www.microsoft.com/download/details.aspx?id=53591). Драйвер является необходимым условием для установки `sqlcmd.exe` и. `bcp.exe`
  
`bcp.exe`и `sqlcmd.exe` устанавливаются `110\Tools` во вложенную папку `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` для версии 11, а `130\Tools` также для 13 и 13,1.

Приложение, использующее функции BCP, должно указывать драйвер из той же версии, которая поставлялась с файлом заголовка и библиотекой, применявшимися при компиляции приложения.  

Например, при компиляции приложения ODBC с помощью `msodbcsql11.lib` и `msodbcsql.h`используйте "Driver = {ODBC Driver 11 for SQL Server}" в строке подключения.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Компоненты Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Windows 
 Драйвер ODBC для Windows состоит из следующих компонентов:
 
|Компонент|Описание|  
|---------------|-----------------|  
|msodbcsql17.dll или <br> msodbcsql13.dll или <br> msodbcsql11.dll|Файл библиотеки динамической компоновки (DLL), содержащий все функциональные возможности драйвера. Этот файл устанавливается в%SYSTEMROOT%\System32.|  
|msodbcdiag17.dll или <br> msodbcdiag13.dll или <br> msodbcdiag11.dll|Файл библиотеки динамической компоновки (DLL), который содержит интерфейс диагностики (трассировки) драйвера. Этот файл устанавливается в%SYSTEMROOT%\System32.|
|msodbcsqlr17.rll или <br> msodbcsqlr13.rll или <br> msodbcsqlr11.rll|Сопутствующий файл ресурса для библиотеки драйвера. Этот файл устанавливается в%SYSTEMROOT%\System32\1033.| 
|s13ch_msodbcsql.chm или <br> s11ch_msodbcsql.chm |Файл справки мастера источников данных, описывающий, как создать источник данных для драйвера. Этот файл устанавливается в%SYSTEMROOT%\System32\1033 <br /> <br /> **Примечание.** Отсутствует CHM-файл для ODBC Driver 17. |  
|msodbcsql.h|Файл заголовка, содержащий все новые определения, необходимые для использования драйвера.<br /><br /> **Примечание**  . Нельзя сослаться на msodbcsql.h и odbcss.h в одной программе.<br /><br /> Файл msodbcsql.h для ODBC Driver 17 или 13 устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK. <br /> Файл msodbcsql.h для ODBC Driver 11 устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.| 
|msodbcsql17.lib или <br> msodbcsql13.lib или <br> msodbcsql11.lib|Файл библиотеки, необходимый для вызова функций служебной программы **bcp**, являющихся частью драйвера.<br /><br /> **Примечание**. Если вы включаете в программу ссылку на этот файл библиотеки, убедитесь в том, что этот файл находится по вашему системному пути, а также по системному пути других пользователей, которые используют это приложение.<br /><br /> Файл msodbcsql17.lib или msodbcsql13.lib устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK.<br /> msodbcsql11.lib устанавливается в папку %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK.|

  
## <a name="see-also"></a>См. также:  
 [Драйвер Microsoft ODBC для SQL Server в Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
