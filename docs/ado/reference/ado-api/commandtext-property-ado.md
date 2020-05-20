---
title: Свойство CommandText (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandText
helpviewer_keywords:
- CommandText property [ADO]
ms.assetid: 4dd7e82a-8da5-4a4e-b439-11a29286fa0e
author: rothja
ms.author: jroth
ms.openlocfilehash: 0fea58e679e11ac068189ad622b3dce627fc8a63
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760441"
---
# <a name="commandtext-property-ado"></a>Свойство CommandText (ADO)
Указывает текст команды, которая должна быть выдана поставщику.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строковое** значение, содержащее команду поставщика, например инструкцию SQL, имя таблицы, относительный URL-адрес или вызов хранимой процедуры. По умолчанию используется пустая строка ("").  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **CommandText** , чтобы задать или вернуть текст команды, представленной объектом [Command](../../../ado/reference/ado-api/command-object-ado.md) . Обычно это будет инструкция SQL, но также может быть любой другой тип инструкции команды, распознаваемый поставщиком, например вызов хранимой процедуры. Инструкция SQL должна иметь определенный диалект или версию, поддерживаемые обработчиком запросов поставщика.  
  
 Если свойство [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md) объекта **Command** имеет значение **true** , а объект **команды** привязан к открытому соединению при задании свойства **CommandText** , то ADO готовит запрос (то есть скомпилированную форму запроса, который хранится поставщиком) при вызове методов [EXECUTE](../../../ado/reference/ado-api/execute-method-ado-command.md) или [Open](../../../ado/reference/ado-api/open-method-ado-connection.md) .  
  
 В зависимости от значения свойства [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) объект ADO может изменить свойство **CommandText** . Вы можете в любое время прочитать свойство **CommandText** , чтобы увидеть фактический текст команды, который ADO будет использовать во время выполнения.  
  
 Используйте свойство **CommandText** , чтобы задать или вернуть относительный URL-адрес, указывающий ресурс, например файл или каталог. Ресурс задается относительно расположения, явно заданного абсолютным URL-адресом, или неявно с помощью открытого объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (Visual c++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Метод Requery](../../../ado/reference/ado-api/requery-method.md)   
 [Пример свойств ActiveConnection, CommandText, CommandTimeout, CommandType, Size и Direction (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
