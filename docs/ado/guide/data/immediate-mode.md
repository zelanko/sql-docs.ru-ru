---
title: Режим интерпретации | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], immediate mode
- immediate mode [ADO]
- updating data [ADO], immediate mode
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3952ef502bf79d6704cbaea80b9a825a3c70981b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925016"
---
# <a name="immediate-mode"></a>Режим интерпретации
Режим интерпретации действует, когда свойство **LockType** имеет значение **adLockOptimistic** или **адлоккпессимистик**. В режиме интерпретации изменения в записи передаются в источник данных сразу после того, как вы объявили работу над строкой, вызвав метод **Update** .  
  
## <a name="calling-update"></a>Вызов обновления  
 Если вы перейдете из записи, которая добавляется или редактируется перед вызовом метода **Update** , то ADO автоматически вызовет **Update** для сохранения изменений. Если необходимо отменить все изменения, внесенные в текущую запись, или удалить вновь добавленную запись, необходимо вызвать метод **CancelUpdate** перед навигацией.  
  
 Текущая запись остается текущей после вызова метода **Update** .  
  
## <a name="cancelupdate"></a>CancelUpdate  
 Используйте метод **CancelUpdate** для отмены всех изменений, внесенных в текущую строку, или для удаления вновь добавленной строки. Нельзя отменить изменения текущей строки или новой строки после вызова метода **Update** , если только изменения не являются частью транзакции, которую можно откатить методом **RollbackTrans** или частью пакетного обновления. В случае пакетного обновления можно отменить **Обновление** с помощью метода **CancelUpdate** или **CancelBatch** .  
  
 При добавлении новой строки при вызове метода **CancelUpdate** текущая строка преобразуется в текущую строку до вызова **AddNew** .  
  
 Если текущая строка не была изменена или добавлена новая строка, вызов метода **CancelUpdate** приведет к ошибке.
