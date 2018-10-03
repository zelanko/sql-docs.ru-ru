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
manager: craigg
ms.openlocfilehash: f2cd74f8912d711b7cd6be93e63aca322172754c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706794"
---
# <a name="set-the-history-retention-period-sql-server-management-studio"></a>настроить срок хранения журнала (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Укажите срок хранения журнала на странице **Общие** диалогового окна **Свойства базы данных распространителя — \<база_данных_распространителя>**. Эта настройка управляет длительностью хранения журнала агента репликации. Эту страницу можно открыть на странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>**. Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-history-retention-period"></a>Указание срока хранения журнала  
  
1.  На странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку свойств (**…**) для базы данных распространителя.  
  
2.  Введите значение в поле **Сохранять журнал производительности репликации не менее** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)  
  
  
