---
title: Сведения о версии & заголовка SQL Server Express LocalDB
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
author: CarlRabeler
ms.author: carlrab
ms.custom: seo-dt-2019
ms.openlocfilehash: f5aeb8a5eda8e4e49e478cbc53cd0ad90e3cc890
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74095479"
---
# <a name="sql-server-express-localdb-header-and-version-information"></a>Заголовок и сведения о версии SQL Server Express LocalDB
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Отдельный файл заголовка для интерфейса API экземпляра SQL Server Express LocalDB отсутствует. Сигнатуры функций LocalDB и коды ошибок определяются в файле заголовка собственного клиента SQL Server (sqlncli.h). Для использования интерфейса API экземпляра LocalDB необходимо включить в проект файл заголовка sqlncli.h.  
  
## <a name="localdb-versioning"></a>Управление версиями LocalDB  
 Установка LocalDB использует по одному набору двоичных файлов на каждую из основных версий SQL Server. Эти версии LocalDB поддерживаются независимо. Исправления в них также вносятся независимо друг от друга. Это значит, что пользователю необходимо указывать используемый базовый выпуск LocalDB (то есть номер основной версии SQL Server). Версия указывается в стандартном формате версии, определяемом классом .NET Framework **System. Version** :  
  
 *Major. minor [. Build [. Редакция]]*  
  
 Первые два числа в строке версии (*основной* и *дополнительный*) являются обязательными. Последние два числа в строке версии (*Сборка* и *Редакция*) являются необязательными и по умолчанию равны нулю, если пользователь оставит их. Это означает, что если пользователь указывает в качестве номера версии LocalDB только "12,2", он будет рассматриваться так, как если бы пользователь указал "12.2.0.0".  
  
 Версия установки LocalDB определяется в разделе реестра MSSQLServer\CurrentVersion, который содержится в разделе реестра экземпляра SQL Server:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL13E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 Поддерживается параллельная работа нескольких версий LocalDB на одной рабочей станции. Однако пользовательский код всегда использует последнюю доступную библиотеку библиотеки **SQLUserInstance** на локальном компьютере для подключения к экземплярам LocalDB.  
  
## <a name="locating-the-sqluserinstance-dll"></a>Поиск DLL-библиотеки SQLUserInstance  
 Для размещения библиотеки DLL **SQLUserInstance** поставщик клиента использует следующий раздел реестра:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 Этот ключ содержит список ключей, по одному для каждой из установленных на компьютере версий LocalDB. Каждый из этих ключей именуется номером версии LocalDB в формате * \<основной версии>*. дополнительный номер версии>(например, ключ [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с именем 13,0). * \<* В каждом из ключей версий содержится пара «имя-значение» `InstanceAPIPath`, определяющая полный путь к установленному в составе соответствующей версии файлу SQLUserInstance.dll. В следующем примере показаны записи реестра для компьютера с установленными версиями LocalDB 11,0 и 13,0:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 Поставщик клиента должен найти последнюю версию всех установленных версий и загрузить DLL-файл **SQLUserInstance** из связанного `InstanceAPIPath` значения.  
  
### <a name="wow64-mode-on-64-bit-windows"></a>Режим WOW64 в 64-разрядной системе Windows  
 У 64-разрядных установок LocalDB имеется дополнительный набор разделов реестра, который позволяет 32-разрядным приложениям, выполняющимся в режиме Windows-32-в-Windows-64 (WOW64), использовать LocalDB. Точнее говоря, в 64-разрядной Windows установщик MSI LocalDB создает следующие разделы реестра:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 64-разрядные программы, `Installed Versions` считывающие ключ, увидят значения, указывающие на 64-разрядные версии библиотеки **SQLUserInstance** DLL, а 32-разрядные программы (работающие в 64-разрядных Windows в режиме WOW64) будут `Installed Versions` автоматически перенаправлены в `Wow6432Node` раздел, расположенный в кусте Hive. Этот ключ содержит значения, указывающие на 32-разрядные версии библиотеки **SQLUserInstance** .  
  
## <a name="using-localdb_define_proxy_functions"></a>Использование константы LOCALDB_DEFINE_PROXY_FUNCTIONS  
 API экземпляра LocalDB определяет константу с именем LOCALDB_DEFINE_PROXY_FUNCTIONS, которая автоматизирует обнаружение и загрузку библиотеки **SQLUserInstance** DLL.  
  
 Раздел кода, включаемый этой константой, содержит реализацию учетных записей-посредников для каждого из интерфейсов API LocalDB. Реализации прокси-сервера используют общую функцию для привязки к точкам входа в последней установленной библиотеке **SQLUserInstance** DLL, а затем перенаправляют запросы.  
  
 Функции учетной записи-посредника включаются лишь в случае, если константа LOCALDB_DEFINE_PROXY_FUNCTIONS определяется в пользовательском коде перед включением файла sqlncli.h. Эту константу следует определять только в одном исходном модуле (CPP-файле), так как она определяет внешние имена функций для всех точек входа интерфейса API. Она предоставляет реализацию прокси-классов для каждого из API-интерфейсов LocalDB.  
  
 В следующем примере кода показано использование макроса из собственного кода C++:  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
...  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
...  
}  
...  
  
```  
  
  
