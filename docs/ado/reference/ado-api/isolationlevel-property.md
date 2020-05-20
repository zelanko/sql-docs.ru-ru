---
title: IsolationLevel, свойство | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::IsolationLevel
helpviewer_keywords:
- IsolationLevel property
ms.assetid: ea84e4b2-fbf2-4eef-b9ce-796b22e21800
author: rothja
ms.author: jroth
ms.openlocfilehash: ea8d538dbd5c4c06cb770a983a2733bb2f27e6b2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758660"
---
# <a name="isolationlevel-property"></a>Свойство IsolationLevel
Указывает уровень изоляции для объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение [исолатионлевеленум](../../../ado/reference/ado-api/isolationlevelenum.md) . Значение по умолчанию — **adXactReadCommitted**.  
  
## <a name="remarks"></a>Примечания  
 Используйте свойство **IsolationLevel** , чтобы установить уровень изоляции объекта **Connection** . Параметр не вступит в силу до следующего вызова метода [примеры BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) . Если запрошенный уровень изоляции недоступен, поставщик может вернуть следующий более высокий уровень изоляции, не обновляя свойство **IsolationLevel** .  
  
 Свойство **IsolationLevel** доступно для чтения и записи.  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании объекта **подключения** на стороне клиента свойство **IsolationLevel** может быть установлено только в **адксактунспеЦифиед**. Поскольку пользователи работают с отключенными объектами **Recordset** в кэше на стороне клиента, могут возникнуть проблемы с многопользовательской работой. Например, когда два разных пользователя пытаются обновить одну и ту же запись, служба Remote Data Service просто позволяет пользователю, который сначала обновляет запись, получить «выиграть». Запрос на обновление второго пользователя завершится с ошибкой.  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств IsolationLevel и Mode (Visual Basic)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [Пример свойств IsolationLevel и Mode (Visual c++)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
