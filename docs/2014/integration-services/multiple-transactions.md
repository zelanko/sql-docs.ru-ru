---
title: Несколько транзакций | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c98fa7454a1a01ee6879a514f369e6fb6c1a0570
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36097588"
---
# <a name="multiple-transactions"></a>Множественные транзакции
  В одном пакете служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] может содержаться несколько самостоятельных транзакций. Каждый раз, когда контейнер в середине иерархии вложенных контейнеров не поддерживает транзакции, контейнеры выше и ниже по иерархии начинают отдельные транзакции, если настроены для поддержки транзакций. Транзакции фиксируются или откатываются, начиная с самой глубокой задачи в иерархии вложенных контейнеров пакета. Однако после фиксации вложенной транзакции она не откатывается, если внешняя транзакция прервана.  
  
## <a name="illustration-of-multiple-transactions"></a>Иллюстрация множественных транзакций  
 Например, пакет включает контейнер последовательности, содержащий два контейнера «цикл по каждому элементу», и каждый контейнер включает две задачи «Выполнение SQL». Контейнеры «цикл по каждому элементу» не поддерживают транзакции, а контейнер последовательности и задача «Выполнение SQL» поддерживают. В данном примере каждая задача «Выполнение SQL» будет выполнять свою собственную транзакцию и не будет подвергаться откату в случае, если транзакция в задаче последовательности окажется прерванной.  
  
 Свойства TransactionOption контейнера последовательности, контейнера "цикл по каждому элементу" и задач "Выполнение SQL" установлены следующим образом:  
  
-   Свойство TransactionOption контейнера последовательности установлено в значение **Required**.  
  
-   Свойства TransactionOption контейнеров "цикл по каждому элементу" установлены в значения **NotSupported**.  
  
-   Свойство TransactionOption задач Execute SQL установлено в значение **Required**.  
  
 На следующей диаграмме показаны пять несвязанных транзакций в пакете. Одна транзакция была начата контейнером последовательности, а четыре других — задачами «Выполнение SQL».  
  
 ![Реализация множественных транзакций](media/mw-dts-trans2.gif "Реализация множественных транзакций")  
  
## <a name="related-tasks"></a>Related Tasks  
 [Настройка пакета для использования транзакций](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  