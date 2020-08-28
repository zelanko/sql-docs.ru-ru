---
description: Объект Error
title: Объект Error | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Error
helpviewer_keywords:
- error object [ADO]
ms.assetid: a175d453-fa55-4f49-9ede-a26d83177919
author: rothja
ms.author: jroth
ms.openlocfilehash: 03f02654e281d052ec8bbb9b8f9df041484cc005
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973665"
---
# <a name="error-object"></a>Объект Error
Содержит сведения об ошибках доступа к данным, относящихся к одной операции, включающей в себя поставщик.  
  
## <a name="remarks"></a>Remarks  
 Любая операция, включающая объекты ADO, может формировать одну или несколько ошибок поставщика. При возникновении каждой ошибки в коллекцию [ошибок](../../../ado/reference/ado-api/errors-collection-ado.md) объекта [Connection](../../../ado/reference/ado-api/connection-object-ado.md) помещаются один или несколько объектов **ошибок** . Если другая операция ADO создает ошибку, коллекция **Errors** удаляется, а новый набор объектов **ошибок** помещается в коллекцию **Errors** .  
  
> [!NOTE]
>  Каждый объект **ошибки** представляет определенную ошибку поставщика, а не ошибку ADO. Ошибки ADO предоставляются механизмом обработки исключений времени выполнения. Например, в Microsoft Visual Basic возникновение ошибки, относящейся к ADO, вызывает событие **On Error** и появляется в объекте **Error** . Полный список ошибок ADO см. в разделе [еррорвалуинум](../../../ado/reference/ado-api/errorvalueenum.md) .  
  
 Вы можете считать свойства объекта **ошибки** , чтобы получить подробные сведения о каждой ошибке, включая следующие.  
  
-   Свойство [Description](../../../ado/reference/ado-api/description-property.md) , содержащее текст ошибки. Это свойство по умолчанию.  
  
-   Свойство [Number](../../../ado/reference/ado-api/number-property-ado.md) , которое содержит **длинное** целое значение константы ошибки.  
  
-   Свойство [Source](../../../ado/reference/ado-api/source-property-ado-error.md) , определяющее объект, вызвавший ошибку. Это особенно полезно при наличии нескольких объектов **Error** в коллекции **Errors** после запроса к источнику данных.  
  
-   Свойства [SQLSTATE](../../../ado/reference/ado-api/sqlstate-property.md) и [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md) , которые предоставляют сведения из источников данных SQL.  
  
 При возникновении ошибки поставщика она помещается в коллекцию **Errors** объекта **Connection** . ADO поддерживает возврат нескольких ошибок с помощью одной операции ADO, чтобы разрешить сведения об ошибках, характерные для поставщика. Чтобы получить эти подробные сведения об ошибке в обработчике ошибок, используйте подходящие функции перехвата ошибок языка или среды, с которыми вы работаете, а затем используйте вложенные циклы для перечисления свойств каждого объекта **Error** в коллекции **Errors** .  
  
> [!NOTE]
>  **Пользователи Microsoft Visual Basic и VBScript** Если нет допустимого объекта **соединения** , необходимо получить сведения об ошибке из объекта **Error** .  
  
 Как и поставщики, ADO очищает объект **сведений об ошибках OLE** перед вызовом, потенциально создающим новую ошибку поставщика. Однако коллекция **Errors** в объекте **Connection** очищается и заполняется только в том случае, если поставщик создает новую ошибку или когда вызывается метод [clear](../../../ado/reference/ado-api/clear-method-ado.md) .  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются как объекты **ошибок** в коллекции **ошибок** , но не приводят к остановке выполнения программы. Перед вызовом методов [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) для объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) ; метод [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) для объекта **Connection** ; или задайте свойство [Filter](../../../ado/reference/ado-api/filter-property.md) для объекта **набора записей** , вызовите метод **clear** для коллекции **Errors** . Таким образом, можно прочитать свойство [Count](../../../ado/reference/ado-api/count-property-ado.md) коллекции **Errors** , чтобы проверить наличие возвращаемых предупреждений.  
  
 Объект **Error** не является надежным для скриптов.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события объекта Error](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Примеры свойств Description, HelpContext, HelpFile, NativeError, Number, Source и SQLState (Visual c++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Приложение А. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
