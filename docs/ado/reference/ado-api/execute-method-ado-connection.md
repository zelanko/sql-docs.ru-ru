---
title: Выполнение метода (объект Connection ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4999b1e21ec145713cadae28ff7ee8a64dd460b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932894"
---
# <a name="execute-method-ado-connection"></a>Метод Execute (объект Connection ADO)
Выполняет указанный запрос, инструкцию SQL, хранимая процедура или поставщика текста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает [объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) ссылка на объект.  
  
#### <a name="parameters"></a>Параметры  
 *CommandText*  
 Объект **строка** значение, содержащее инструкцию SQL, хранимая процедура, URL-адрес или текст поставщика для выполнения. **При необходимости**, имена таблиц можно использовать только, если поставщик SQL виду. Например, если имя таблицы из «Customers» используется, ADO автоматически привяжет стандартный синтаксис SQL Select для формирования и передачи «ВЫБЕРИТЕ * из клиентов» как [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции к поставщику.  
  
 *RecordsAffected*  
 Необязательный. Объект **Long** переменной, в которой поставщик возвращает количество записей, затронутых операцией.  
  
 *Параметры*  
 Необязательный параметр. Объект **Long** значение, указывающее, как поставщик должен оценить аргумент CommandText. Может быть битовой маской, из одного или нескольких [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) или [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) значения.  
  
 **Примечание** используйте **ExecuteOptionEnum** значение **adExecuteNoRecords** для повышения производительности, сводя к минимуму внутренней обработки и для приложений, переносе из Visual Basic 6.0.  
  
 Не используйте **adExecuteStream** с **Execute** метод **подключения** объекта.  
  
 Не используйте значения CommandTypeEnum adCmdFile или adCmdTableDirect с Execute. Эти значения могут использоваться только как параметры с [метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [метод Requery](../../../ado/reference/ado-api/requery-method.md) методы **записей**.  
  
## <a name="remarks"></a>Примечания  
 С помощью **Execute** метод [объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) объект выполняет любой запрос, который передается методу в качестве аргумента CommandText для указанного подключения. Если CommandText аргумент указывает, возвращающие строки запроса, все результаты, приводит к возникновению ошибки выполнения хранятся в новом **записей** объекта. Если команда не предназначен для возврата результатов (например, запроса SQL UPDATE) поставщик возвращает **ничего не** условии, что параметр **adExecuteNoRecords** указан; в противном случае Execute которого возвращает Закрыто **записей**.  
  
 Возвращенный **записей** всегда — это только для чтения, однопроходный курсор. При необходимости **записей** со дополнительные функциональные возможности, сначала создайте **записей** с параметрами требуемых свойств, а затем использовать **набор записей** объекта [ Метод (объект Recordset ADO) Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) метод для выполнения запроса и возвращения требуемого типа курсора.  
  
 Содержание *CommandText* аргумент, характерные для поставщика и может быть стандартный синтаксис SQL или любой формат специальные команды, поддерживаемыми поставщиком.  
  
 Событие ExecuteComplete будет выдаваться при завершении этой операции.  
  
> [!NOTE]
>  URL-адреса, с использованием схемы http, автоматически вызывает метод [поставщик Microsoft OLE DB для публикаций в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
