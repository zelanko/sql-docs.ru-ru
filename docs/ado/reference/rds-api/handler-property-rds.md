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
ms.openlocfilehash: 653e29f8666f63cd4867b11b378ee8711f8b0508
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606444"
---
# <a name="handler-property-rds"></a>Свойство Handler (служба удаленных рабочих столов)
Указывает имя программы Настройка на сервере (обработчик), который расширяет функциональность [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)и любые параметры, используемые объектом *обработчик*.  
  
 **Область применения:** [объекта DataControl (служба удаленных рабочих СТОЛОВ)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
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
  
 Альтернатива параметра **обработчик** будет указать обработчик и параметры в свойство [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) свойство; т. е «**обработчик = *** handlerName, parameter1, параметр2...;* ".  
  
## <a name="applies-to"></a>Объект применения  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Пример свойства Handler (Visual Basic)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [Настройка DataFactory](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


