---
title: "Ошибка объекта | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Error
helpviewer_keywords:
- error object [ADO]
ms.assetid: a175d453-fa55-4f49-9ede-a26d83177919
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00f04d9ccdfd4547e7d207edc21db44a4e04508b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="error-object"></a>Объект Error
Содержит сведения об ошибках доступа к данным, которые относятся к одной операции с участием поставщика.  
  
## <a name="remarks"></a>Remarks  
 Любая операция, включающее объекты ADO можно создать одну или несколько ошибок поставщика. Как возникли ошибки, один или несколько **ошибка** объекты размещаются в [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Если другая операция ADO создает ошибку, **ошибки** коллекция очищается и новый набор **ошибка** объектов помещается в **ошибки** коллекции.  
  
> [!NOTE]
>  Каждый **ошибка** представляет ошибку конкретного поставщика, а не ошибка ADO. Ошибки ADO предоставляется механизм обработки исключений во время выполнения. Например, в Visual Basic возникновение ошибки конкретного ADO активируют **On Error** событий и отображаются в **ошибка** объекта. Полный список ошибок ADO см. в разделе [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) раздела.  
  
 Можно прочитать **ошибка** свойств объекта, чтобы получить подробные сведения о каждой ошибке, включая следующие:  
  
-   [Описание](../../../ado/reference/ado-api/description-property.md) свойство, содержащее сообщение об ошибке. Это свойство по умолчанию.  
  
-   [Номер](../../../ado/reference/ado-api/number-property-ado.md) свойство, содержащее **длинные** целочисленное значение константы ошибки.  
  
-   [Источника](../../../ado/reference/ado-api/source-property-ado-error.md) свойство, которое определяет объект, который вызвал ошибку. Это особенно полезно, если существует несколько **ошибка** объекты в **ошибки** коллекции следующий запрос к источнику данных.  
  
-   [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) и [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md) свойств, предоставляющих сведения из источников данных SQL.  
  
 При возникновении ошибки поставщика, он помещается в **ошибки** коллекцию **подключения** объекта. ADO поддерживает возврат нескольких ошибок с помощью одной операции ADO, разрешающее сообщения об ошибках, относящиеся к поставщику. Для получения этих сведений об ошибке в обработчик ошибок, используйте соответствующие функции перехват ошибок языка или среды, вы работаете с, а затем использовать вложенные циклы для перечисления свойств каждого **ошибка** объекта в **Ошибки** коллекции.  
  
> [!NOTE]
>  **Microsoft Visual Basic и пользователей VBScript** Если нет допустимых **подключения** объекта, необходимо получить сведения об ошибке из **ошибка** объекта.  
  
 Так же, как поставщики этого ADO очищает **сведения OLE ошибке** объекта после вызова, потенциально может создать новую ошибку поставщика. Тем не менее **ошибки** коллекции на **подключения** очищается и заполняется только в том случае, если поставщик создает новую ошибку, или если объект [снимите](../../../ado/reference/ado-api/clear-method-ado.md) вызывается метод.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются в виде **ошибка** объекты в **ошибки** коллекции, но не остановить выполнение программы. Перед вызовом метода [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта; [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод **подключения** задана объекта; или [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **записей** , вызовите **снимите**метод **ошибки** коллекции. Таким образом, можно прочитать [число](../../../ado/reference/ado-api/count-property-ado.md) свойство **ошибки** коллекцию для проверки возникли предупреждения.  
  
 **Ошибка** объект не является безопасным для создания сценариев.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Error](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Описание, HelpContext, файл справки, NativeError, номер, источника и пример свойства SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, файл справки, NativeError, номер, источник и пример свойства SQLState (VC ++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Коллекция ошибок (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
