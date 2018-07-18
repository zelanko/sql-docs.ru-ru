---
title: Выполнить метод (соединение ADO) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27d3f5318d093d18312dd531421f5c32755aeaf1
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278143"
---
# <a name="execute-method-ado-connection"></a>Выполнить метод (соединение ADO)
Выполняет указанный запрос, инструкции SQL, хранимая процедура или поставщика текста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [объекта набора записей (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) ссылку на объект.  
  
#### <a name="parameters"></a>Параметры  
 *commandText*  
 Объект **строка** значение, содержащее инструкцию SQL, хранимая процедура, URL-адрес или поставщика текста для выполнения. **При необходимости**, имена таблиц можно использовать только, если поставщик является поставщиком SQL виду. Для примера Если имя таблицы «Заказчики» используется, ADO автоматически вставляет стандартный синтаксис SQL Select для формирования и передачи «ВЫБЕРИТЕ * из заказчики» как [!INCLUDE[tsql](../../../includes/tsql_md.md)] инструкции для поставщика.  
  
 *RecordsAffected*  
 Необязательный параметр. Объект **длинные** переменной, в которой поставщик возвращает количество записей, затронутых операцию.  
  
 *Параметры*  
 Необязательный параметр. Объект **длинные** значение, указывающее, как поставщик должен оценить аргумент CommandText. Может быть битовой маской, одного или нескольких [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) или [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения.  
  
 **Примечание** используйте **ExecuteOptionEnum** значение **adExecuteNoRecords** для повышения производительности путем минимизации внутренней обработки и для приложений, которые перенос приложений из Visual Basic 6.0.  
  
 Не используйте **adExecuteStream** с **Execute** метод **подключения** объекта.  
  
 Не используйте значения CommandTypeEnum adCmdFile или adCmdTableDirect с Execute. Эти значения можно использовать только как параметры с [метода Open (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery-метод](../../../ado/reference/ado-api/requery-method.md) методы **записей**.  
  
## <a name="remarks"></a>Примечания  
 С помощью **Execute** метод [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) объекта выполняет любой запрос, который передается методу в качестве аргумента CommandText для указанного подключения. Если аргумент CommandText указывает, возвращающей строки запроса, все результаты, приводит к возникновению ошибки выполнения хранятся в новый **записей** объекта. Если команда не является возвращать результаты (например, запрос SQL UPDATE) поставщик возвращает **ничего** , пока параметр **adExecuteNoRecords** указан; в противном случае выполняется возвращает Закрыто **записей**.  
  
 Возвращенный **записей** объект всегда является только для чтения, однонаправленный курсор. При необходимости **записей** объекта с более широкими функциональными возможностями, сначала создайте **записей** объекта с параметрами нужное свойство, а затем использовать **записей** объекта [ Open-метод (набора записей ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод для выполнения запроса и возвращения требуемого типа курсора.  
  
 Содержимое *CommandText* аргумент, характерные для поставщика и может быть стандартный синтаксис SQL или любого формата специальная команда, поддерживаемых поставщиком.  
  
 При возникновении события ExecuteComplete будет выдаваться при эта операция завершается.  
  
> [!NOTE]
>  URL-адреса, с помощью схемы http автоматически вызывает [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
