---
title: MSSQL_ENG021330 | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021330 error
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 05a2b45668efdd1bcef6b30e009d8248cb96e2be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620979"
---
# <a name="mssqleng021330"></a>MSSQL_ENG021330
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21330|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Не удалось создать вложенный каталог в рабочем каталоге репликации.(%ls)|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка может произойти при ручной инициализации подписки, существует ошибка при создании каталога, в котором хранятся скрипты репликации. Ошибка может быть вызвана недостатком разрешений: если инициализация подписки выполняется без применения моментального снимка, то учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на издателе, должна обладать разрешением на запись в папку моментальных снимков распространителя.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте правильность указанного пути к папке моментальных снимков, а также убедитесь, что учетная запись, под которой работает служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, обладает всеми необходимыми разрешениями.  
  
## <a name="see-also"></a>См. также:  
 [Указание расположения моментальных снимков по умолчанию (SQL Server Management Studio)](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Инициализация транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
