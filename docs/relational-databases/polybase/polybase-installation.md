---
title: Установка PolyBase на компьютере под управлением Windows | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
helpviewer_keywords:
- PolyBase, installation
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 6783112203e5c63aae41749f942da6240265eea3
ms.sourcegitcommit: 1a4aa8d2bdebeb3be911406fc19dfb6085d30b04
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872304"
---
# <a name="install-polybase-on-windows"></a>Установка PolyBase на компьютере по управлением Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Чтобы установить пробную версию SQL Server, перейдите на страницу [ознакомительных версий SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016). 
   
## <a name="prerequisites"></a>предварительные требования  
   
- 64-разрядный выпуск SQL Server Evaluation.  
   
- Microsoft .NET Framework 4.5.  

- Среда выполнения Oracle Java SE (JRE). Поддерживаются версии 7 (начиная с 7.51) и 8. Среды [JRE](https://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html) и [Server JRE](https://www.oracle.com/technetwork/java/javase/downloads/server-jre8-downloads-2133154.html) должны работать. Откройте страницу [Загрузка Java SE](https://www.oracle.com/technetwork/java/javase/downloads/index.html). Если JRE отсутствует, произойдет сбой установщика. JRE9 и JRE10 не поддерживаются.

- Минимальный объем памяти: 4 ГБ. 
   
- Минимум места на жестком диске: 2 ГБ.
  
- Рекомендации как минимум 16 ГБ ОЗУ.
   
- Для корректной работы PolyBase должен быть включен протокол TCP/IP. TCP/IP включен по умолчанию во всех выпусках SQL Server, кроме Developer и Express. Для корректной работы PolyBase в выпусках Developer и Express нужно включить подключение по TCP/IP. См. раздел [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).

- MSVC++ 2012. 

> [!NOTE]
> 
> PolyBase можно установить только на одном экземпляре SQL Server на компьютере.
> 
> [!IMPORTANT]
> 
> Чтобы использовать функцию передачи вычислений в Hadoop, в целевом кластере Hadoop должны быть базовые компоненты HDFS, YARN и MapReduce с включенным сервером журнала заданий. PolyBase отправляет запрос на передачу через MapReduce и получает сведения о состоянии c сервера журнала заданий. Без любого из этих компонентов запрос завершится сбоем.
  
## <a name="single-node-or-polybase-scale-out-group"></a>Один узел или масштабируемая группа PolyBase

Прежде чем устанавливать PolyBase на экземплярах SQL Server, вам следует выбрать режим этой установки: на одном узле или в [масштабируемой группе PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).

Для использования масштабируемой группы PolyBase необходимо следующее.

- Все компьютеры должны быть в одном домене.
- При установке PolyBase учетная запись и пароль будут одни и те же.
- Экземпляры SQL Server могут взаимодействовать друг с другом по сети.
- Экземпляры SQL Server имеют одинаковую версию SQL Server.

Установить PolyBase можно либо на одном узле, либо в масштабируемой группе, и после установки изменить это нельзя. Для изменения потребуется удалить и вновь установить компонент.

## <a name="use-the-installation-wizard"></a>Использование мастера установки
   
1. Запустите файл setup.exe для SQL Server.   
   
2. Щелкните **Установка**, затем **Новая установка автономного SQL Server или добавление компонентов**.  
   
3. На странице выбора компонентов выберите пункт **Служба запросов PolyBase для внешних данных**.  

   ![Службы PolyBase](../../relational-databases/polybase/media/install-wizard.png "Службы PolyBase")  
   
4. На странице конфигурации сервера настройте **службу SQL Server PolyBase Engine** и **службу перемещения данных SQL Server PolyBase** на запуск под одной и той же учетной записью домена.  
   
   > [!IMPORTANT] 
   >
   >В масштабируемой группе PolyBase служба PolyBase Engine и служба перемещения данных PolyBase должны работать на всех узлах под одной учетной записью домена. См. раздел [Масштабируемые группы PolyBase](#enable).
   
5. На странице конфигурации PolyBase выберите один из двух вариантов. Дополнительные сведения: [Масштабируемые группы PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).  
   
   - Использование экземпляра SQL Server в качестве автономного экземпляра с поддержкой PolyBase.  
   
     Выберите этот вариант, чтобы использовать экземпляр SQL Server в качестве изолированного головного узла.  
   
   - Использование экземпляра SQL Server в составе масштабируемой группы PolyBase Этот вариант позволит брандмауэру разрешить входящие подключения. Будут разрешены подключения к ядру СУБД SQL Server, SQL Server PolyBase Engine, службе перемещения данных SQL Server PolyBase и обозревателю SQL. Брандмауэр также разрешит входящие подключения с других узлов в масштабируемой группе PolyBase.  
   
     Кроме того, при выборе этого варианта в брандмауэре будут включены подключения для координатора распределенных транзакций Майкрософт (MSDTC) и будут изменены параметры реестра для MSDTC.  
   
6. На странице конфигурации PolyBase укажите диапазон портов (не менее шести). Программа установки SQL Server выделяет первые шесть доступных портов из указанного диапазона.  

   > [!IMPORTANT]
   >
   > После установки необходимо [включить компонент PolyBase](#enable).


##  <a name="installing"></a> Использование командной строки

Используйте значения из этой таблицы для создания сценариев установки. Служба SQL Server PolyBase Engine и служба перемещения данных SQL Server PolyBase должны работать под одной и той же учетной записью. В масштабируемой группе PolyBase обе службы PolyBase должны выполняться на всех узлах под одной доменной учетной записью.  
   
<!--SQL Server 2016/2017-->
::: moniker range="= sql-server-2016 || = sql-server-2017"

|Компонент SQL Server|Параметр и значения|Описание|  
|--------------------------|--------------------------|-----------------|  
|Управление программой установки SQL Server|**Обязательно**<br /><br /> /FEATURES=PolyBase|Выбирает компонент PolyBase.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCACCOUNT|Задает учетную запись для службы ядра. По умолчанию используется **NT Authority\NETWORK SERVICE**.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCPASSWORD|Задает пароль для учетной записи службы ядра.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCSTARTUPTYPE|Задает режим запуска для PolyBase Engine: Automatic (Автоматически, используется по умолчанию), Disabled (Отключено) или Manual (Вручную).|  
|Перемещение данных SQL Server PolyBase |**Необязательно**<br /><br /> /PBDMSSVCACCOUNT|Задает учетную запись для службы перемещения данных. Значение по умолчанию — **NT Authority\NETWORK SERVICE**.|  
|Перемещение данных SQL Server PolyBase |**Необязательно**<br /><br /> /PBDMSSVCPASSWORD|Задает пароль для учетной записи службы перемещения данных.|  
|Перемещение данных SQL Server PolyBase |**Необязательно**<br /><br /> /PBDMSSVCSTARTUPTYPE|Задает режим запуска для службы перемещения данных: Automatic (Автоматически, используется по умолчанию), Disabled (Отключено) или Manual (Вручную).|  
|PolyBase|**Необязательно**<br /><br /> /PBSCALEOUT|Указывает, используется ли этот экземпляр SQL Server в составе масштабируемой вычислительной группы PolyBase. <br />Поддерживаемые значения: True, False.|  
|PolyBase|**Необязательно**<br /><br /> /PBPORTRANGE|Указывает диапазон портов (не менее шести) для служб PolyBase. Пример<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end
<!--SQL Server 2019-->
::: moniker range=">= sql-server-ver15 || =sqlallproducts-allversions"

|Компонент SQL Server|Параметр и значения|Описание|  
|--------------------------|--------------------------|-----------------|  
|Управление программой установки SQL Server|**Обязательно**<br /><br /> /FEATURES=PolyBaseCore, PolyBaseJava, PolyBase | PolyBaseCore обеспечивает поддержку всех возможностей PolyBase, кроме подключения к Hadoop. PolyBaseJava обеспечивает подключение к Hadoop. PolyBase обеспечивает поддержку всех возможностей. |  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCACCOUNT|Задает учетную запись для службы ядра. По умолчанию используется **NT Authority\NETWORK SERVICE**.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCPASSWORD|Задает пароль для учетной записи службы ядра.|  
|Компонент SQL Server PolyBase Engine|**Необязательно**<br /><br /> /PBENGSVCSTARTUPTYPE|Задает режим запуска для PolyBase Engine: Automatic (Автоматически, используется по умолчанию), Disabled (Отключено) или Manual (Вручную).|  
|Перемещение данных SQL Server PolyBase |**Необязательно**<br /><br /> /PBDMSSVCACCOUNT|Задает учетную запись для службы перемещения данных. Значение по умолчанию — **NT Authority\NETWORK SERVICE**.|  
|Перемещение данных SQL Server PolyBase |**Необязательно**<br /><br /> /PBDMSSVCPASSWORD|Задает пароль для учетной записи службы перемещения данных.|  
|Перемещение данных SQL Server PolyBase |**Необязательно**<br /><br /> /PBDMSSVCSTARTUPTYPE|Задает режим запуска для службы перемещения данных: Automatic (Автоматически, используется по умолчанию), Disabled (Отключено) или Manual (Вручную).|  
|PolyBase|**Необязательно**<br /><br /> /PBSCALEOUT|Указывает, используется ли этот экземпляр SQL Server в составе масштабируемой вычислительной группы PolyBase. <br />Поддерживаемые значения: True, False.|  
|PolyBase|**Необязательно**<br /><br /> /PBPORTRANGE|Указывает диапазон портов (не менее шести) для служб PolyBase. Пример<br /><br /> `/PBPORTRANGE=16450-16460`|  

::: moniker-end

После установки необходимо [включить компонент PolyBase](#enable).



**Пример**

Далее представлен пример сценария установки.  

```cmd
   
Setup.exe /Q /ACTION=INSTALL /IACCEPTSQLSERVERLICENSETERMS /FEATURES=SQLEngine,PolyBase   
/INSTANCENAME=MSSQLSERVER /SQLSYSADMINACCOUNTS="\<fabric-domain>\Administrator"   
/INSTANCEDIR="C:\Program Files\Microsoft SQL Server" /PBSCALEOUT=TRUE   
/PBPORTRANGE=16450-16460 /SECURITYMODE=SQL /SAPWD="<StrongPassword>"   
/PBENGSVCACCOUNT="<DomainName>\<UserName>" /PBENGSVCPASSWORD="<StrongPassword>"   
/PBDMSSVCACCOUNT="<DomainName>\<UserName>" /PBDMSSVCPASSWORD="<StrongPassword>"  
   
```  

## <a id="enable"></a> Включение PolyBase

Завершив установку, включите компонент PolyBase для доступа к его функциям. Чтобы подключиться к SQL Server 2019 CTP 2.0, нужно включить PolyBase после установки. Используйте следующую команду Transact-SQL.


```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE [ WITH OVERRIDE ]  ;
```
Затем потребуется перезапустить экземпляр.


## <a name="post-installation-notes"></a>Примечания после установки  

PolyBase устанавливает три пользовательские базы данных: DWConfiguration, DWDiagnostics и DWQueue. Эти базы данных предназначены для PolyBase. Не изменяйте и не удаляйте их.  
   
### <a id="confirminstall"></a> Как подтвердить установку  

Выполните следующую команду. Если служба PolyBase установлена, возвращается значение 1. В противном случае возвращается 0.  

```sql  
SELECT SERVERPROPERTY ('IsPolyBaseInstalled') AS IsPolyBaseInstalled;  
```  

### <a name="firewall-rules"></a>Правила брандмауэра  

Программа установки SQL Server PolyBase создает на компьютере следующие правила брандмауэра:  
   
- SQL Server PolyBase — ядро СУБД — \<имя_экземпляра_SQL_Server> (входящие TCP-соединения);  
   
- SQL Server PolyBase — службы PolyBase — \<имя_экземпляра_SQL_Server> (входящие TCP-соединения);  

- SQL Server PolyBase — обозреватель SQL — (UDP вход.).  
   
Эти правила активируются во время установки, если экземпляр SQL Server входит в масштабируемую группу PolyBase. Брандмауэр будет открыт для входящих подключений. Будут разрешены подключения к ядру СУБД SQL Server, SQL Server PolyBase Engine, службе перемещения данных SQL Server PolyBase и обозревателю SQL. Но если во время установки служба брандмауэра на компьютере не запущена, программа установки SQL Server не сможет включить эти правила. В этом случае запустите службу брандмауэра и включите эти правила после установки.  
   
#### <a name="to-enable-the-firewall-rules"></a>Включение правил брандмауэра  

1. Откройте **Панель управления**.  

2. Щелкните **Система и безопасность** и выберите **Брандмауэр Windows**.  
   
3. Щелкните **Дополнительные параметры**, а затем выберите **Правила для входящих подключений**.  
   
4. Щелкните отключенное правило правой кнопкой мыши и выберите **Включить правило**.  
   
### <a name="polybase-service-accounts"></a>Учетные записи служб PolyBase

Чтобы изменить учетные записи служб для PolyBase Engine и служб перемещения данных PolyBase, удалите и вновь установите компонент PolyBase.

## <a name="next-steps"></a>Следующие шаги  

См. раздел [PolyBase configuration](../../relational-databases/polybase/polybase-configuration.md).
