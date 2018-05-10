---
title: Кластеризация DTC для групп доступности SQL Server 2016 | Документы Майкрософт
ms.custom: ''
ms.date: 08/30/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a47c5005-20e3-4880-945c-9f78d311af7a
caps.latest.revision: 3
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 50ba8074a718beb3722daaff67f224bd0d5c5c66
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="cluster-dtc-for-sql-server-2016-availability-groups"></a>Кластеризация DTC для групп доступности SQL Server 2016

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этом разделе описываются требования и шаги для кластеризации службы координатора распределенных транзакций (DTC) (Майкрософт) для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Дополнительные сведения о распределенных транзакциях и [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] см. в разделе [Транзакции между базами данных и распределенные транзакции для групп доступности AlwaysOn и зеркального отображения базы данных (SQL Server)](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md).

 ## <a name="checklist-preliminary-requirements"></a>Контрольный список: предварительные требования
||Задача|Справочник|  
|------|-----------------|----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Убедитесь, что все узлы, службы и группа доступности были настроены правильно.|[Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)|
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Убедитесь, что выполнены требования для DTC группы доступности.|[Транзакции между базами данных и распределенные транзакции для групп доступности AlwaysOn и зеркального отображения базы данных (SQL Server)](../../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)

## <a name="checklist-clustered-dtc-resource-dependencies"></a>Контрольный список: зависимости кластеризованных ресурсов DTC
||Задача|Справочник|  
|------|-----------------|----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Диск общего хранилища.|[Настройка диска общего хранилища](https://msdn.microsoft.com/library/cc982358(v=bts.10).aspx). Рекомендуется использовать букву диска **M**.|
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Уникальный ресурс сетевого имени DTC.  Имя будет зарегистрировано как объект-компьютер кластера в Active Directory.<br /><br />Убедитесь, что выполняется одно из следующих условий:<br /><br />• Пользователь, создающий ресурс сетевого имени DTC, имеет разрешение на создание объектов-компьютеров для подразделения или контейнера, где будет размещаться ресурс сетевого имени DTC.<br /><br />• Если у пользователя нет разрешения на создание объектов-компьютеров, попросите администратора домена предварительно подготовить объект-компьютер кластера для ресурса сетевого имени DTC.|[Предварительная подготовка кластеризованных объектов-компьютеров в доменных службах Active Directory](https://technet.microsoft.com/library/dn466519(v=ws.11).aspx)|
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Допустимый и доступный статический IP-адрес и соответствующая маска подсети.||

## <a name="cluster-the-dtc-resource"></a>Кластеризация ресурса DTC
После создания ресурса группы доступности ресурса следует создать кластеризованный ресурс DTC и добавить его в группу доступности.  Пример скрипа можно найти в разделе [Создание кластеризованного DTC для группы доступности AlwaysOn](../../../database-engine/availability-groups/windows/create-clustered-dtc-for-an-always-on-availability-group.md).


## <a name="checklist-post-clustered-dtc-resource-configurations"></a>Контрольный список: публикация конфигураций кластеризованного ресурса DTC
||Задача|Справочник|  
|------|-----------------|----------|  
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Включение безопасного сетевого доступа для кластеризованного ресурса DTC.|[Включение безопасного сетевого доступа для MS DTC](https://technet.microsoft.com/library/cc753620(v=ws.10).aspx)|
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Остановка и отключение локальной службы DTC.|[Настройка запуска службы](https://technet.microsoft.com/library/cc755249(v=ws.11).aspx)|
|![Флажок](../../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|Отключение и включение службы SQL Server для каждого экземпляра в группе доступности.  Отработка отказа группы доступности при необходимости.|[Выполнение запланированного перехода на другой ресурс вручную для группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)<br /><br />[Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](../../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)|

- Если запущен сервер Windows Server 2012 R2, к ОС должна быть применена [KB 3030373](http://support.microsoft.com/kb/3090973) .

- Серверы для групп доступности должны быть подготовлены в соответствии с контрольными списками в разделе [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).

- Должны быть настроены экземпляры серверов для [**групп доступности AlwaysOn**](../../../database-engine/availability-groups/windows/configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md).

### <a name="resources"></a>РЕСУРСЫ


[Дополнительные сведения о тестировании DTC в группах доступности:](https://blogs.technet.microsoft.com/dataplatform/2016/01/25/sql-server-2016-dtc-support-in-availability-groups/)

[Отслеживание групп доступности](monitor-availability-groups-transact-sql.md)

[Создание группы доступности](create-an-availability-group-transact-sql.md)


[SQL Server 2016 DTC Support in Availability Groups](http://blogs.technet.microsoft.com/dataplatform/2016/01/25/sql-server-2016-dtc-support-in-availability-groups/) (Поддержка DTC для SQL Server 2016 в группах доступности) 

[Внешняя ссылка: Configure DTC for a clustered instance of SQL Server with Windows Server 2008 R2](http://sqlha.com/2013/03/12/how-to-properly-configure-dtc-for-clustered-instances-of-sql-server-with-windows-server-2008-r2/) (Настройка DTC для кластеризованного экземпляра SQL Server с Windows Server 2008 R2)
