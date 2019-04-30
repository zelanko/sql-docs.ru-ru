---
title: Свойство Handler (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 642addb5ff03e17b5b36e7baa01ef87661a00b35
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63276451"
---
# <a name="handler-property-rds"></a>Свойство Handler (служба удаленных рабочих столов)
Указывает имя программы Настройка на сервере (обработчик), который расширяет функциональность [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)и любые параметры, используемые объектом *обработчик*.  
  
 **Область применения:** [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектную переменную, которая представляет [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) объекта.  
  
 *String*  
 Объект **строка** значение, содержащее имя обработчика и все параметры всех разделенных запятыми (например, `"handlerName,parm1,parm2,...,parm` *N*`"`).  
  
## <a name="remarks"></a>Примечания  
 Это свойство поддерживает [настройки](../../../ado/guide/remote-data-service/datafactory-customization.md), функции, которым требуется параметр [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) свойства **adUseClient**.  
  
 Имя обработчика и его параметрах, если таковые имеются, разделяются запятыми («",»"). Приведет к непредсказуемому поведению, если точки с запятой («;») находится в любом положении в *строка*. Можно написать собственный обработчик, если он поддерживает **IDataFactoryHandler** интерфейс.  
  
 Имя обработчика по умолчанию — **MSDFMAP. Обработчик**, и его параметр по умолчанию является файл настройки с именем **MSDFMAP. INI**. Это свойство используется для вызова альтернативный настройки файлы, созданные администратором сервера.  
  
 Альтернатива параметра **обработчик** будет указать обработчик и параметры в свойство [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство; т. е "**обработчик =** _handlerName параметр1, параметр2,...;_".  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Handler (Visual Basic)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


