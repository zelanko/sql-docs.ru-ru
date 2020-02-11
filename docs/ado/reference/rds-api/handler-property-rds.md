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
ms.openlocfilehash: a7423879b8263d87575d913c4863143faf3573e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964006"
---
# <a name="handler-property-rds"></a>Свойство Handler (служба удаленных рабочих столов)
Указывает имя программы настройки на стороне сервера (обработчик), которая расширяет функциональные возможности [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)данных и всех параметров, используемых *обработчиком*.  
  
 Область **применения:** [объект элемента управления (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>Параметры  
 *DataControl*  
 Объектная переменная, представляющая [RDS. Объект элемента управления](../../../ado/reference/rds-api/datacontrol-object-rds.md) .  
  
 *String*  
 **Строковое** значение, содержащее имя обработчика и все параметры, разделенные запятыми (например, `"handlerName,parm1,parm2,...,parm` *N*`"`).  
  
## <a name="remarks"></a>Remarks  
 Это свойство поддерживает [настройку](../../../ado/guide/remote-data-service/datafactory-customization.md), которая требует установки свойства [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) в значение **адусеклиент**.  
  
 Имя обработчика и его параметров, если таковые имеются, разделяются запятыми (","). Непредсказуемое поведение приведет к тому, что точка с запятой (";") появляется в любом месте *строки*. Вы можете написать собственный обработчик, если он поддерживает интерфейс **идатафакторихандлер** .  
  
 Имя обработчика по умолчанию — **мсдфмап. И его**параметр по умолчанию — файл настройки с именем **мсдфмап. INI**. Это свойство используется для вызова альтернативных файлов настройки, созданных администратором сервера.  
  
 Альтернативой заданию свойства **обработчика** является указание обработчика и параметров в свойстве [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) . то есть "**handler =**_хандлернаме, параметр1, параметр2,...;_".  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataControl (служба удаленных рабочих столов)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойства Handler (Visual Basic)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [Настройка в отношении фактов](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


