---
title: Объект Error | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bc9dc5f19dacfb6fbdab8c2e0dd8278cbc4b97b3
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66719279"
---
# <a name="error-object"></a>Объект Error
Содержит сведения об ошибках доступа к данным, которые относятся к одной операции с участием поставщика.  
  
## <a name="remarks"></a>Примечания  
 Любая операция, включающее объекты ADO можно создать один или несколько ошибок поставщика. Так как возникли ошибки, один или несколько **ошибка** объекты размещаются в [ошибки](../../../ado/reference/ado-api/errors-collection-ado.md) коллекцию [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта. Если другая операция ADO создает ошибку, **ошибки** коллекции установлен и новый набор **ошибка** объектов помещается в **ошибки** коллекции.  
  
> [!NOTE]
>  Каждый **ошибка** представляет ошибку конкретного поставщика, а не ошибка ADO. Ошибки ADO предоставляются механизм обработки исключений среды выполнения. Например, в Microsoft Visual Basic, возникновение ошибки ADO конкретных активирует **On Error** событий и отображаются в **ошибка** объекта. Полный список ошибок ADO, см. в разделе [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) раздела.  
  
 Можно прочитать **ошибка** свойств объекта, чтобы получить подробные сведения о каждой ошибке, включая следующие:  
  
-   [Описание](../../../ado/reference/ado-api/description-property.md) свойство, содержащее текст сообщения об ошибке. Это свойство по умолчанию.  
  
-   [Номер](../../../ado/reference/ado-api/number-property-ado.md) свойство, содержащее **Long** целое число для константы ошибки.  
  
-   [Источника](../../../ado/reference/ado-api/source-property-ado-error.md) свойство, которое определяет объект, который вызвал ошибку. Это особенно полезно, если существует несколько **ошибка** объекты в **ошибки** коллекции следуя запрос к источнику данных.  
  
-   [SQLState](../../../ado/reference/ado-api/sqlstate-property.md) и [NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md) свойства, которые предоставляют информацию из источников данных SQL.  
  
 При возникновении ошибки поставщика, он помещается в **ошибки** коллекцию **подключения** объекта. ADO поддерживает возврат нескольких ошибок по одной операции ADO, чтобы разрешить сообщения об ошибках поставщика. Для получения этих сведений подробных сведений об ошибках в обработчик ошибок, используйте соответствующие перехват ошибок компонента языка или среды, вы работаете, а затем использовать вложенные циклы для перечисления свойства каждого **ошибка** объекта в **Ошибки** коллекции.  
  
> [!NOTE]
>  **Microsoft Visual Basic и VBScript пользователей** Если отсутствует **подключения** объекта, необходимо получить сведения об ошибке из **ошибка** объекта.  
  
 Так же, как поставщики сделать, очищает ADO **OLE Error Info** объекта после выполнения звонка, который потенциально может создать новую ошибку поставщика. Тем не менее **ошибки** коллекции **подключения** объекта очищается и заполняется только в том случае, когда поставщик создает новую ошибку, или когда [Очистить](../../../ado/reference/ado-api/clear-method-ado.md) вызывается метод.  
  
 Некоторые свойства и методы возвращают предупреждения, которые отображаются в виде **ошибка** объекты в **ошибки** коллекции, но не приостанавливает выполнение программы. Перед вызовом метода [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), или [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) методы [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта; [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md) метод **подключения** задана объекта; или [фильтра](../../../ado/reference/ado-api/filter-property.md) свойство **записей** , вызовите **снимите**метод **ошибки** коллекции. Таким образом, можно прочитать [число](../../../ado/reference/ado-api/count-property-ado.md) свойство **ошибки** коллекцию для проверки возникли предупреждения.  
  
 **Ошибка** объект не является безопасным для использования в сценариях.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события объекта Error](../../../ado/reference/ado-api/error-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Description, HelpContext, HelpFile, NativeError, номер, источника и SQLState свойства пример (Visual Basic)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Описание, HelpContext, HelpFile, NativeError, номер, источника и пример свойства SQLState (Visual C++)](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Коллекция Errors (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Приложение а. Поставщики](../../../ado/guide/appendixes/appendix-a-providers.md)
