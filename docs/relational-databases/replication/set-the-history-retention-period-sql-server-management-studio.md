---
title: Настройка срока хранения журнала (SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- history retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: c288daab-5181-4d4b-ba2a-8a147098e758
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 9a33317c8f430a3665c47e94441e8f78c68085c6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768383"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>настроить срок хранения журнала (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Укажите срок хранения журнала на странице **Общие** диалогового окна **Свойства базы данных распространителя — \<база_данных_распространителя>** . Эта настройка управляет длительностью хранения журнала агента репликации. Эту страницу можно открыть на странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** . Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Указание срока хранения журнала  
  
1.  На странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку свойств ( **…** ) для базы данных распространителя.  
  
2.  Введите значение в поле **Сохранять журнал производительности репликации не менее** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
  
  
