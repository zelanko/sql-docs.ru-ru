---
title: SQL Server Express LocalDB заголовок и сведения о версии | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apilocation:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e261b75d2746ac24cd8520d67ebc3d6d7d5c09f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sql-server-express-localdb-header-and-version-information"></a>Заголовок и сведения о версии SQL Server Express LocalDB
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Отдельный файл заголовка для интерфейса API экземпляра SQL Server Express LocalDB отсутствует. Сигнатуры функций LocalDB и коды ошибок определяются в файле заголовка собственного клиента SQL Server (sqlncli.h). Для использования интерфейса API экземпляра LocalDB необходимо включить в проект файл заголовка sqlncli.h.  
  
## <a name="localdb-versioning"></a>Управление версиями LocalDB  
 Установка LocalDB использует по одному набору двоичных файлов на каждую из основных версий SQL Server. Эти версии LocalDB поддерживаются независимо. Исправления в них также вносятся независимо друг от друга. Это значит, что пользователю необходимо указывать используемый базовый выпуск LocalDB (то есть номер основной версии SQL Server). Версия, указанная в стандартном формате версии определенные платформой .NET Framework **System.Version** класса:  
  
 *следующий вид: основная.Дополнительная[.построение[.редакция]]*  
  
 Первые два числа в строке версии (*основных* и *дополнительный*) являются обязательными. Последние два числа в строке версии (*построения* и *редакции*) являются необязательными и по умолчанию равным нулю, если пользователь не указывает их. Это значит, что при указании пользователем номера версии LocalDB «12.2» считается, что задана версия «12.2.0.0».  
  
 Версия установки LocalDB определяется в разделе реестра MSSQLServer\CurrentVersion, который содержится в разделе реестра экземпляра SQL Server:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL13E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 Поддерживается параллельная работа нескольких версий LocalDB на одной рабочей станции. Однако пользовательский код всегда использует последние **SQLUserInstance** DLL на локальном компьютере для подключения к экземплярам LocalDB.  
  
## <a name="locating-the-sqluserinstance-dll"></a>Поиск DLL-библиотеки SQLUserInstance  
 Чтобы найти **SQLUserInstance** библиотека DLL, поставщик клиента использует следующий раздел реестра:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 Этот ключ содержит список ключей, по одному для каждой из установленных на компьютере версий LocalDB. Каждый из этих разделов называется номерам версий LocalDB в формате  *\<основной номер версии >*. *\<номер_дополнительной_версии >* (например, ключ для [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] называется 13.0). В каждом из ключей версий содержится пара «имя-значение» `InstanceAPIPath`, определяющая полный путь к установленному в составе соответствующей версии файлу SQLUserInstance.dll. Ниже приведен пример записи реестра для компьютера, который имеет версий LocalDB 11.0 и 13.0 установлен.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 Поставщик клиента должен найти среди всех установленных версий и загрузить последнюю версию **SQLUserInstance** DLL-файл из соответствующей `InstanceAPIPath` значение.  
  
### <a name="wow64-mode-on-64-bit-windows"></a>Режим WOW64 в 64-разрядной системе Windows  
 У 64-разрядных установок LocalDB имеется дополнительный набор разделов реестра, который позволяет 32-разрядным приложениям, выполняющимся в режиме Windows-32-в-Windows-64 (WOW64), использовать LocalDB. Точнее говоря, в 64-разрядной Windows установщик MSI LocalDB создает следующие разделы реестра:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\13.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\130\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 64-разрядные программы чтения `Installed Versions` ключа будут отображены значения, указывающие на 64-разрядной версии **SQLUserInstance** библиотеки DLL, хотя 32-разрядные программы (выполняющиеся в 64-разрядной версии Windows в режиме WOW64) автоматически перенаправляются на `Installed Versions` ключ в компоненте `Wow6432Node` hive. Этот раздел содержит значения, указывающие на 32-разрядные версии **SQLUserInstance** DLL.  
  
## <a name="using-localdbdefineproxyfunctions"></a>Использование константы LOCALDB_DEFINE_PROXY_FUNCTIONS  
 API экземпляра LocalDB определяет константу localdb_define_proxy_functions, автоматизирующую обнаружение и загрузку **SqlUserInstance** DLL.  
  
 Раздел кода, включаемый этой константой, содержит реализацию учетных записей-посредников для каждого из интерфейсов API LocalDB. Реализации прокси-сервера используют общую функцию для привязки к точкам входа в самой новой установленной **SqlUserInstance** библиотеки DLL и последующего перенаправления запросов.  
  
 Функции учетной записи-посредника включаются лишь в случае, если константа LOCALDB_DEFINE_PROXY_FUNCTIONS определяется в пользовательском коде перед включением файла sqlncli.h. Эту константу следует определять только в одном исходном модуле (CPP-файле), так как она определяет внешние имена функций для всех точек входа интерфейса API. Она предоставляет реализацию прокси-классов для каждого из API-интерфейсов LocalDB.  
  
 В следующем примере кода показано использование макроса из собственного кода C++:  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
…  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
…  
}  
…  
  
```  
  
  
