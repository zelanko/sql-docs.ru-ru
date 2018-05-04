---
title: Управление транзакциями (XMLA) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d34410453fea22927b36ed7791830f170a0a3a09
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="managing-transactions-xmla"></a>Управление транзакциями (XMLA)
  Каждый XML для аналитики (XMLA) команду, отправленную экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняется в контексте транзакции в рамках текущего явного или неявного сеанса. Для управления каждой из этих транзакций используется [BeginTransaction](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md), [CommitTransaction](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md), и [RollbackTransaction](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md) команд. При помощи этих команд можно создавать явные или неявные транзакции, изменять счетчик ссылок транзакции, а также запускать, фиксировать или выполнять откат транзакций.  
  
## <a name="implicit-and-explicit-transactions"></a>Явные и неявные транзакции  
 Транзакция является либо неявной, либо явной.  
  
 **Неявные транзакции**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Создает *неявное* транзакцию для XML для Аналитики команды, если **BeginTransaction** команда не указывает начало транзакции. Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] всегда фиксируют неявную транзакцию, если команда будет выполнена успешно, и откатывают неявную транзакцию при сбое команды.  
  
 **Явная транзакция**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Создает *явных* транзакции при **BeginTransaction** команда запускает транзакцию. Тем не менее [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] фиксируют явную транзакцию, только если **CommitTransaction** отправляется команда и откат явной транзакции, если **RollbackTransaction** отправляется команда.  
  
 Кроме того, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] выполняют откат и неявных, и явных транзакций, если текущий сеанс завершается до выполнения активной транзакции.  
  
## <a name="transactions-and-reference-counts"></a>Транзакции и счетчики ссылок  
 Службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ведут счетчик ссылок транзакций для каждого сеанса. Однако службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не поддерживают вложенные транзакции, поэтому ведется только одна активная транзакция на сеанс. Если текущий сеанс не имеет активной транзакции, счетчик ссылок транзакции устанавливается в нуль.  
  
 Другими словами, каждая **BeginTransaction** команда увеличивает счетчик ссылок на единицу при каждом **CommitTransaction** команда уменьшает на единицу. Если **CommitTransaction** команда устанавливает счетчик транзакций в нуль, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] фиксирует транзакцию.  
  
 Тем не менее **RollbackTransaction** команда выполняет откат активной транзакции независимо от текущего значения счетчика ссылок транзакций. Другими словами, один **RollbackTransaction** команда выполняет откат активной транзакции независимо от того, сколько **BeginTransaction** команды или **CommitTransaction** команды были отправлены и устанавливает счетчик ссылок транзакции в нуль.  
  
## <a name="beginning-a-transaction"></a>Запуск транзакции  
 **BeginTransaction** команда начинает явную транзакцию в текущем сеансе и увеличивает счетчик ссылок транзакции для текущего сеанса на единицу. Все последующие команды считаются внутри активной транзакции, пока не будет достаточно **CommitTransaction** команды отправляются зафиксировать транзакцию, или один **RollbackTransaction**отправки команды для отката активной транзакции.  
  
## <a name="committing-a-transaction"></a>Фиксация транзакции  
 **CommitTransaction** команда фиксирует результаты команд, выполняемых после **BeginTransaction** в текущем сеансе была выполнена команда. Каждый **CommitTransaction** команда уменьшает счетчик ссылок для активных транзакций в сеансе. Если **CommitTransaction** команда устанавливает счетчик до нуля, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] фиксирует активную транзакцию. Если нет активной транзакции (другими словами, счетчик ссылок транзакции для текущего сеанса уже равно нулю), **CommitTransaction** команды приведет к ошибке.  
  
## <a name="rolling-back-a-transaction"></a>Откат транзакции  
 **RollbackTransaction** команда выполняет откат результатов команд, выполняемых после **BeginTransaction** в текущем сеансе была выполнена команда. **RollbackTransaction** команда выполняет откат активной транзакции независимо от того, текущий счетчик ссылок транзакции и устанавливает счетчик ссылок транзакции в нуль. Если нет активной транзакции (другими словами, счетчик ссылок транзакции для текущего сеанса уже равно нулю), **RollbackTransaction** команды приведет к ошибке.  
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XML для Аналитики в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
