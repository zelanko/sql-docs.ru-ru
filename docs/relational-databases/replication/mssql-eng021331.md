---
title: MSSQL_ENG021331 | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021331 error
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 9e75adaa3ead3e081955d5797c4640a2a072d439
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363221"
---
# <a name="mssql_eng021331"></a>MSSQL_ENG021331
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21331|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Не удалось скопировать файл пользовательского скрипта на распространитель.(%ls)|  
  
## <a name="explanation"></a>Объяснение  
 Данная ошибка может возникнуть, когда подписка инициализирована вручную, и скрипты, сформированные репликацией или заданные в команде репликации, не могут быть сохранены в указанный каталог. Ошибка может быть вызвана недостатком разрешений: если инициализация подписки выполняется без применения моментального снимка, то учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на издателе, должна обладать разрешением на запись в папку моментальных снимков распространителя.  
  
## <a name="user-action"></a>Действие пользователя  
 Проверьте правильность указанного пути к папке моментальных снимков, а также убедитесь, что учетная запись, под которой работает служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, обладает всеми необходимыми разрешениями.  
  
## <a name="see-also"></a>См. также:  
 [Указание параметров моментального снимка](../../relational-databases/replication/snapshot-options.md)   
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Инициализация транзакционной подписки без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
