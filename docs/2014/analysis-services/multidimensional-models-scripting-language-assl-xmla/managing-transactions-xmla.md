---
title: Управление транзакциями (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XML for Analysis, transactions
- XMLA, transactions
- explicit transactions [XMLA]
- implicit transactions
- transactions [XML for Analysis]
- rolling back transactions, XMLA
- reference counts [XML for Analysis]
- committing transactions
- starting transactions
ms.assetid: f5112e01-82f8-4870-bfb7-caa00182c999
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fefda354d9f596c92a06673e7692bb840f582071
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167615"
---
# <a name="managing-transactions-xmla"></a>Управление транзакциями (XMLA)
  Каждый XML для аналитики (XMLA) команды, отправляемые экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняется в контексте транзакции в рамках текущего явного или неявного сеанса. Для управления каждой из этих транзакций используйте [BeginTransaction](../xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../xmla/xml-elements-commands/committransaction-element-xmla.md), и [RollbackTransaction](../xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) команды. При помощи этих команд можно создавать явные или неявные транзакции, изменять счетчик ссылок транзакции, а также запускать, фиксировать или выполнять откат транзакций.  
  
## <a name="implicit-and-explicit-transactions"></a>Явные и неявные транзакции  
 Транзакция является либо неявной, либо явной.  
  
 **Неявные транзакции**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Создает *неявное* транзакцию для XML для Аналитики команды, если `BeginTransaction` команда не указывает начало транзакции. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] всегда фиксируют неявную транзакцию, если команда будет выполнена успешно, и откатывают неявную транзакцию при сбое команды.  
  
 **Явная транзакция**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Создает *явные* транзакции если `BeginTransaction` команда запускает транзакцию. При этом службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] фиксируют явную транзакцию, только если отправлена команда `CommitTransaction`, и выполняют ее откат, если отправлена команда `RollbackTransaction`.  
  
 Кроме того, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняют откат и неявных, и явных транзакций, если текущий сеанс завершается до выполнения активной транзакции.  
  
## <a name="transactions-and-reference-counts"></a>Транзакции и счетчики ссылок  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ведут счетчик ссылок транзакций для каждого сеанса. Однако службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживают вложенные транзакции, поэтому ведется только одна активная транзакция на сеанс. Если текущий сеанс не имеет активной транзакции, счетчик ссылок транзакции устанавливается в нуль.  
  
 Другими словами, каждая команда `BeginTransaction` увеличивает счетчик ссылок на единицу, а каждая команда `CommitTransaction` уменьшает его на единицу. Если команда `CommitTransaction` устанавливает счетчик транзакций в нуль, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] фиксируют транзакцию.  
  
 При этом команда `RollbackTransaction` выполняет откат активной транзакции без учета текущего значения счетчика ссылок транзакций. Другими словами, одна команда `RollbackTransaction` выполняет откат активной транзакции независимо от того, сколько было отправлено команд `BeginTransaction` или `CommitTransaction`, и устанавливает счетчик ссылок транзакции в нуль.  
  
## <a name="beginning-a-transaction"></a>Запуск транзакции  
 Команда `BeginTransaction` начинает явную транзакцию в рамках текущего сеанса и увеличивает счетчик ссылок транзакции для текущего сеанса на единицу. Считается, что все последующие команды выполняются в рамках активной транзакции, пока не будет отправлено достаточное количество команд `CommitTransaction`, чтобы зафиксировать транзакцию, или одна команда `RollbackTransaction`, чтобы выполнить откат активной транзакции.  
  
## <a name="committing-a-transaction"></a>Фиксация транзакции  
 Команда `CommitTransaction` фиксирует результаты команд, выполняемых после того, как в рамках текущего сеанса была выполнена команда `BeginTransaction`. Каждая команда `CommitTransaction` уменьшает счетчик ссылок транзакции для активной транзакции в рамках сеанса. Если команда `CommitTransaction` устанавливает счетчик транзакций в нуль, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] фиксируют активную транзакцию. Если отсутствуют активные транзакции (то есть счетчик ссылок на транзакции в текущем сеансе уже имеет нулевое значение), команда `CommitTransaction` вызывает ошибку.  
  
## <a name="rolling-back-a-transaction"></a>Откат транзакции  
 Команда `RollbackTransaction` осуществляет откат результатов команд, выполненных после того, как в текущем сеансе была выполнена команда `BeginTransaction`. Команда `RollbackTransaction` выполняет откат активной транзакции независимо от текущего значения счетчика ссылок транзакции и устанавливает счетчик ссылок транзакции в нуль. Если отсутствуют активные транзакции (то есть счетчик ссылок на транзакции в текущем сеансе уже имеет нулевое значение), команда `RollbackTransaction` вызывает ошибку.  
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
