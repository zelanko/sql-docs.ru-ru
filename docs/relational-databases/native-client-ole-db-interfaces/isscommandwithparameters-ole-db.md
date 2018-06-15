---
title: Интерфейс ISSCommandWithParameters (OLE DB) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db-interfaces
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
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
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6d90f4cdfd9ac42291da9bf6694a2786000ba8d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32948999"
---
# <a name="isscommandwithparameters-ole-db"></a>Интерфейс ISSCommandWithParameters (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Интерфейс**ISSCommandWithParameters** обеспечивает поддержку [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML и определяемых пользователем типов данных. Этот дополнительный интерфейс наследует основной интерфейс OLE DB, **ICommandWithParameters**. Помимо трех методов, наследуемых из интерфейса **ICommandWithParameters**( **GetParameterInfo**, **MapParameterNames**и **SetParameterInfo**), интерфейс **ISSCommandWithParameters** содержит два новых метода, которые используются для обработки серверных типов данных.  
  
> [!NOTE]  
>  Интерфейс **ISSCommandWithParameters** может использоваться при применении компонентов службы, однако сами компоненты службы этот интерфейс не используют.  
  
|Метод|Description|  
|------------|-----------------|  
|[ISSCommandWithParameters::GetParameterProperties & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)|Возвращает одну структуру набора свойств **SSPARAMPROPS** в массиве для каждого определяемого пользователем типа данных или XML-параметра, переданного команде, однако для других типов параметров не возвращается ничего.|  
|[ISSCommandWithParameters::SetParameterProperties & #40; OLE DB & #41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)|Задает свойства параметров для каждого параметра в отдельности по порядковому номеру либо задает свойства всех параметров сразу путем указания массива структур **SSPARAMPROPS** .|  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы & #40; OLE DB & #41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)   
 [Использование типов данных XML](../../relational-databases/native-client/features/using-xml-data-types.md)   
 [Использование определяемых пользователем типов](../../relational-databases/native-client/features/using-user-defined-types.md)  
  
  
