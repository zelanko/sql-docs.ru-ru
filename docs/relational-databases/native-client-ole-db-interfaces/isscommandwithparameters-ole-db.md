---
title: ISSCommandWithParameters (OLE DB) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISSCommandWithParameters (OLE DB)
apitype: COM
helpviewer_keywords:
- ISSCommandWithParameters interface
ms.assetid: 3419b7f3-36a3-4863-816e-e641e4e90496
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 308cfc4fd396ee587939057c17dd0fdfbbc18f27
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085972"
---
# <a name="isscommandwithparameters-ole-db"></a>Интерфейс ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **ISSCommandWithParameters** обеспечивает поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов (UDT). Этот дополнительный интерфейс наследует основной интерфейс OLE DB, **ICommandWithParameters**. Помимо трех методов, наследуемых из интерфейса **ICommandWithParameters**( **GetParameterInfo**, **MapParameterNames**и **SetParameterInfo**), интерфейс **ISSCommandWithParameters** содержит два новых метода, которые используются для обработки серверных типов данных.  
  
> [!NOTE]  
>  Интерфейс **ISSCommandWithParameters** может использоваться при применении компонентов службы, однако сами компоненты службы этот интерфейс не используют.  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Возвращает одну структуру набора свойств **SSPARAMPROPS** в массиве для каждого определяемого пользователем типа данных или XML-параметра, переданного команде, однако для других типов параметров не возвращается ничего.|  
|[ISSCommandWithParameters::SetParameterProperties &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Задает свойства параметров для каждого параметра в отдельности по порядковому номеру либо задает свойства всех параметров сразу путем указания массива структур **SSPARAMPROPS** .|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы &#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Использование типов данных XML](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [Использование определяемых пользователем типов](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
