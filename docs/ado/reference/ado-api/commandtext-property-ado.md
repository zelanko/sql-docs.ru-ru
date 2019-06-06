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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7ebc6a783aa8520c3ab16465143acdf1a6bf6628
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698948"
---
# <a name="commandtext-property-ado"></a>Свойство CommandText (ADO)
Указывает текст команды для выполнен по отношению к поставщику.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Возвращает или задает **строка** значение, содержащее команды поставщика, например инструкцию SQL, имя таблицы, относительный URL-адрес или вызов хранимой процедуры. Значение по умолчанию является пустой строкой (»»).  
  
## <a name="remarks"></a>Примечания  
 Используйте **CommandText** свойство задает или возвращает текст команды, представленный [команда](../../../ado/reference/ado-api/command-object-ado.md) объекта. Обычно это будет инструкция SQL, но также может быть любой другой тип инструкция команды, распознаваемым поставщиком, такие как вызов хранимой процедуры. Оператор SQL должен быть определенный, диалект или версию, поддерживаемую обработчиком запросов поставщика.  
  
 Если [подготовленных](../../../ado/reference/ado-api/prepared-property-ado.md) свойство **команда** имеет значение **True** и **команда** объект привязан к открытое соединение при установке **CommandText** свойства ADO подготавливает запроса (то есть скомпилированную форму запроса, который хранится у поставщика) при вызове [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) или [откройте](../../../ado/reference/ado-api/open-method-ado-connection.md)методы.  
  
 В зависимости от [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) может изменить задание, свойство ADO **CommandText** свойство. Можно прочитать **CommandText** свойство в любое время, чтобы просмотреть действительный текст команды ADO, будет использоваться во время выполнения.  
  
 Используйте **CommandText** свойство задание или возврат указать относительный URL-адрес ресурса, например файла или каталога. Ресурс является относительно расположения, явно указан абсолютный URL-адрес или неявно открытую [подключения](../../../ado/reference/ado-api/connection-object-ado.md) объекта.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление свойства пример (Visual Basic)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление пример свойства (Visual C++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Requery-метод](../../../ado/reference/ado-api/requery-method.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, размер и направление примеры свойств (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
