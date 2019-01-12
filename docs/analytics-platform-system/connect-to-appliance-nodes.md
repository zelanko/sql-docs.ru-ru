---
title: Подключение к устройству узлов - Analytics Platform System | Документация Майкрософт
description: В этой статье рассматриваются различные способы для подключения к каждому узлу в Analytics Platform System appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e8c61bebd6265d25e2c3fe0a14516e986f3ee414
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124449"
---
# <a name="connect-to-appliance-nodes-in-analytics-platform-system"></a>Подключение к узлам устройства в Analytics Platform System
В этой статье рассматриваются различные способы для подключения к каждому узлу в Analytics Platform System appliance.  
  
## <a name="connecting-with-hadoop"></a>Соединение с помощью Hadoop  
Прежде чем использовать Hadoop с помощью SQL Server PDW, обратитесь к администратору устройства, чтобы установить среду выполнения Java на SQL Server PDW. Инструкции см. в разделе [Настройка подключения PolyBase к внешним данным &#40;Analytics Platform System&#41; ](configure-polybase-connectivity-to-external-data.md) руководства пользователя устройства.  
  
## <a name="ConnectingToIndividualNodes"></a>Подключение к узлам устройства  
Каждый из узлов устройства осуществляется напрямую только в определенные сценарии использования и определенных пользователем типов. Ниже перечислены каждый узел устройства и сценарии, при которых пользователи будут подключаться непосредственно к этому узлу.  
  
<!-- MISSING LINKS For information on the purpose of each node, see [Understanding SQL Server PDW &#40;SQL Server PDW&#41;](../sqlpdw/understanding-sql-server-pdw-sql-server-pdw.md).  -->  
  
|||  
|-|-|  
|**Node**|**Сценариев доступа**|  
|Управляющий узел|Используйте веб-браузер для доступа к консоли администрирования, которая выполняется на узле управления. Дополнительные сведения см. в разделе [мониторинг устройства с помощью консоли администрирования &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Все клиентские приложения и средства подключения к узлу, независимо от того, использует ли подключение Ethernet или InfiniBand.<br /><br />Чтобы настроить Ethernet-подключение к узлу, используйте элемент управления узла IP-адрес кластера и порт **17001**. Например «192.168.0.1,17001».<br /><br />Чтобы настроить подключение к InfiniBand к управляющему узлу, используйте  <strong>*appliance_domain*-SQLCTL01</strong> и порт **17001**. С помощью  <strong>*appliance_domain*-SQLCTL01</strong>, устройством DNS-сервер будет подключить сервер к активной сети InfiniBand. Чтобы настроить сервер не является специализированным для использования, см. в разделе [Настройка сетевых адаптеров InfiniBand](configure-infiniband-network-adapters.md).<br /><br />Администратор устройства подключается к узлу для выполнения операций управления. Например администратор приложения выполняет следующие операции в управляющем узле:<br /><br />Настройка системы платформы аналитики с **dwconfig.exe** средство настройки.|  
|Вычислительный узел|Вычислительный узел подключения направляются управляющим узлом. IP-адресов, вычислительных узлов никогда не вводятся в команды приложения в качестве параметров.<br /><br />Для загрузки, резервное копирование, копирование удаленной таблицы и Hadoop, SQL Server PDW отправку или получение данных непосредственно в параллельном режиме между вычислительные узлы и узлы, не связанных с устройством или серверов. Эти приложения соединения с SQL Server PDW, подключившись к узлу управления и затем узел элемента управления направляет SQL Server PDW для установления связи между вычислительными узлами и не является специализированным сервером.<br /><br />Например эти операции передачи данных, обеспечивающего параллельную прямые соединения на вычислительных узлах:<br /><br />Загрузка с сервера загрузки для SQL Server PDW.<br /><br />Резервное копирование базы данных из SQL Server PDW на резервный сервер.<br /><br />Восстановление базы данных из резервной копии сервера SQL Server PDW.<br /><br />Запрос данных Hadoop из SQL Server PDW.<br /><br />Экспорт данных из SQL Server PDW к внешней таблице Hadoop.<br /><br />Копирование таблицы SQL Server PDW в удаленной базе данных SMP SQL Server.|  
  
## <a name="connecting-to-the-ethernet-and-infiniband-networks"></a>Подключение к сети InfiniBand и Ethernet  
Удаленные серверы можно подключиться через сеть InfiniBand устройства или через сеть Ethernet. Для повышения производительности, загрузка серверов, резервное копирование серверов и серверов, получать данные через **создать REMOTE TABLE AS SELECT** инструкций, обычно передачи данных через сеть InfiniBand устройства.  
  
Можно настроить серверы не является специализированным принадлежать собственного клиента рабочей группы или домена и затем использовать собственную сеть клиента для подключения к этих серверов и передачи данных на них. Кроме того не связанных с устройством серверов, подключенных к устройству InfiniBand иметь возможность передавать данные друг с другом по сети InfiniBand устройства; Будьте внимательны, так как он может привести к снижению производительности SQL Server PDW.  
  
Например Эта инструкция добавляет сетевые учетные данные для выполнения резервного копирования через InfiniBand на сервер резервного копирования, InfiniBand IP-адрес 192.168.0.1. Домен устройства — *mypdw*, и инструкция выполняется с сервера архивации. Перед выполнением этой инструкции, ее потребуется указать в ней свои параметры.  
  
```  
sqlcmd -S "mypdw-sqlctl01,17001" -U sa -P password -I -Q "exec sp_pdw_add_network_credentials '192.168.0.1', 'mypdw\Administrator', 'password'"  
```  
  
Например команда загрузка начнется со следующими:  
  
```  
dwloader -S mypdw-SQLCTL01  
```  
  
<!-- MISSING LINKS ## See Also  
[Configure an External Windows System To Receive Remote Table Copies Using InfiniBand &#40;SQL Server PDW&#41;](../sqlpdw/configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband-sql-server-pdw.md)  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
