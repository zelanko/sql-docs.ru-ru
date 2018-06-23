---
title: Наследовать транзакции | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [Integration Services], inherited
- child packages
- inherited transactions [Integration Services]
ms.assetid: 90db5564-d41e-4cfe-8c9e-4e68d41eff1c
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0df0ba113b23e9b5cc582b1795299a0befee4bae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189114"
---
# <a name="inherited-transactions"></a>Наследуемые транзакции
  Пакет может запускать другой пакет с помощью задачи «Выполнение пакета». Дочерний пакет, то есть пакет, запускаемый задачей «Выполнение пакета», может создавать собственную транзакцию пакетов или наследовать родительскую транзакцию.  
  
 Дочерний пакет наследует родительскую транзакцию пакетов, если выполняются оба приведенных ниже условия:  
  
-   Пакет вызывается задачей «Выполнение пакета».  
  
-   Задача «Выполнение пакета», вызвавшая пакет, также присоединяется к родительской транзакции пакета.  
  
 Контейнеры и задачи в дочернем пакете не могут присоединяться к родительской транзакции пакетов, если только к ней не присоединяется сам дочерний пакет.  
  
## <a name="illustration-of-package-transactions"></a>Иллюстрация к пакетным транзакциям  
 Все три пакета, показанные на приведенной ниже диаграмме, используют транзакции. Каждый пакет содержит несколько задач. Чтобы выделить поведение транзакций, показаны только задачи «Выполнение пакета». Пакет A запускает пакеты B и C. В свою очередь пакет B запускает пакеты D и E, а пакет C запускает пакет F.  
  
 Пакеты и задачи имеют следующие атрибуты транзакции:  
  
-   Параметру**TransactionOption** присвоено значение **Required** для пакетов A и C  
  
-   Параметру**TransactionOption** присвоено значение **Supported** в пакетах B и D, а также в задачах выполнения пакетов B, D и F.  
  
-   Параметру**TransactionOption** присвоено значение **NotSupported** в пакете E, а также в задачах выполнения пакетов C и E.  
  
 ![Поток унаследованных транзакций](media/mw-dts-executepack.gif "Поток унаследованных транзакций")  
  
 Наследовать транзакции от родительских пакетов могут только пакеты B, D и F.  
  
 Пакеты B и D наследуют транзакцию, запущенную пакетом A.  
  
 Пакет F наследует транзакцию, запущенную пакетом C.  
  
 Пакеты A и C управляют своими собственными транзакциями.  
  
 Пакет E не использует транзакции.  
  
## <a name="related-tasks"></a>Related Tasks  
 [Настройка пакета для использования транзакций](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  