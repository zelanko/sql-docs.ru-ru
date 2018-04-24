---
title: Основные группы доступности (группы доступности AlwaysOn) | Документы Майкрософт
ms.custom: ''
ms.date: 02/01/2018
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: availability-groups
ms.reviewer: ''
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 285adbc7-ac9b-40f6-b4a9-3f1591d3b632
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e63ba118f2b27bd20c5c707749289b77e94f9576
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="basic-availability-groups-always-on-availability-groups"></a>Базовые группы доступности (группы доступности AlwaysOn)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Базовые группы доступности AlwaysOn предоставляют решение высокой доступности для SQL Server 2016 и SQL Server 2017 Standard. Основная группа доступности обеспечивает функционирование среды отработки отказа для одной базы данных. Базовые группы создаются и управляются так же, как обычные (расширенные) [группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) в выпуске Enterprise Edition. В этом документе описаны отличия и ограничения основных групп доступности.  
  
## <a name="features"></a>Компоненты  
 Базовые группы доступности AlwaysOn заменяют нерекомендуемую функцию зеркального отображения базы данных и предоставляют такой же уровень поддержки. Основные группы доступности позволяют поддерживать одну реплику базы данных-источника. Эта реплика может использовать режим синхронной или асинхронной фиксации. Дополнительные сведения о режимах доступности см. в разделе [Режимы доступности (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md). Вторичная реплика остается неактивной, пока нет необходимости отработки отказа. При такой отработке первичная и вторичная роли меняются местами, в результате чего вторичная реплика становится первичной активной базой данных. Дополнительные сведения об отработке отказа см. в разделе [Отработка отказа и режимы отработки отказа (группы доступности AlwaysOn)](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md). Основные группы доступности могут работать в гибридной среде, охватывающей локальные данные и облако Microsoft Azure.  
  
## <a name="limitations"></a>Ограничения  
 Набор возможностей основных групп доступности включает часть возможностей расширенных групп доступности из SQL Server 2016 Enterprise Edition. Для основных групп доступности действуют следующие ограничения.  
  
- Ограничение двух реплик (первичная и вторичная).  
  
- Отсутствует доступ для чтения вторичной реплики.  
  
- Отсутствует возможность резервного копирования вторичной реплики.  

- Отсутствуют проверки целостности на вторичных репликах. 

- Отсутствует поддержка реплик, размещенных на серверах под управлением SQL Server версии ниже SQL Server 2016 Community Technology Preview 3 (CTP3).  

- Поддержка одной базы данных доступности.  
  
- Основные группы доступности не могут быть обновлены до расширенных групп доступности. В этом случае группу необходимо удалить и повторно добавить в группу, содержащую серверы под управлением SQL Server 2016 Enterprise Edition.  
  
- Основные группы доступности поддерживаются только для серверов с ПО выпуска Standard Edition. 

- Основные группы доступности не могут быть частью распределенной группы доступности. 
  
## <a name="configuration"></a>Конфигурация  
 Базовые группы доступности AlwaysOn можно создать на любых двух серверах SQL Server 2016 Standard Edition. В процессе создания основной группы доступности вам потребуется указать обе реплики.  
  
 Чтобы создать базовую группу доступности, используйте команду transact-SQL **CREATE AVAILABILITY GROUP** и укажите параметр **WITH BASIC** (значение параметра по умолчанию — **ADVANCED**). Дополнительные сведения см. в разделе [CREATE AVAILABILITY GROUP (Transact-SQL)](../../../t-sql/statements/create-availability-group-transact-sql.md). В настоящее время в SQL Server Management Studio не предусмотрен пользовательский интерфейс для создания основных групп доступности.  
  
> [!NOTE]  
>  При использовании команды **CREATE AVAILABILITY GROUP** с параметром **WITH BASIC** применяются соответствующие ограничения основных групп доступности. Например, при попытке создания основной группы доступности с доступом для чтения появится ошибка. Таким же образом действуют и другие ограничения. Подробности см. в разделе "Ограничения" этого документа.  
  
## <a name="see-also"></a>См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
