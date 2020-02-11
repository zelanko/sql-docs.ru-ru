---
title: Метод Execute (подключение ADO) | Документация Майкрософт
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932894"
---
# <a name="execute-method-ado-connection"></a>Метод Execute (объект Connection ADO)
Выполняет указанный запрос, инструкцию SQL, хранимую процедуру или специфический для поставщика текст.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает ссылку на объект [объекта Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
#### <a name="parameters"></a>Параметры  
 *CommandText*  
 **Строковое** значение, содержащее инструкцию SQL, хранимую процедуру, URL-адрес или определяемый поставщиком текст для выполнения. **При необходимости**можно использовать имена таблиц, но только в том случае, если поставщик поддерживает SQL. Например, если используется имя таблицы «Customers», то ADO автоматически добавляет стандартный синтаксис SQL SELECT для формирования и передачи "SELECT * FROM Customers" в качестве [!INCLUDE[tsql](../../../includes/tsql-md.md)] инструкции поставщику.  
  
 *RecordsAffected*  
 Необязательный параметр. **Длинная** переменная, к которой поставщик возвращает количество записей, затронутых операцией.  
  
 *Параметры*  
 Необязательный параметр. Значение **типа Long** , указывающее, как поставщик должен оценивать аргумент CommandText. Может быть битовой маской одного или нескольких значений [коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md) или [ексекутеоптионенум](../../../ado/reference/ado-api/executeoptionenum.md) .  
  
 **Примечание** . Используйте значение **Ексекутеоптионенум** **адексекутенорекордс** для повышения производительности за счет минимизации внутренней обработки и для приложений, которые вы переносите из Visual Basic 6,0.  
  
 Не используйте **адексекутестреам** с методом **EXECUTE** объекта **Connection** .  
  
 Не используйте значения Коммандтипинум для Адкмдфиле или Адкмдтабледирект с Execute. Эти значения можно использовать только в качестве параметров с методами методов запроса [Open (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) и [Requery](../../../ado/reference/ado-api/requery-method.md) для **набора записей**.  
  
## <a name="remarks"></a>Remarks  
 При использовании метода **EXECUTE** для объекта [соединения объект (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) выполняет любой запрос, передаваемый в метод в аргументе CommandText для указанного соединения. Если аргумент CommandText задает запрос, возвращающий строку, все результаты, формируемые выполнением, сохраняются в новом объекте **набора записей** . Если команда не должна возвращать результаты (например, запрос SQL UPDATE), поставщик возвращает **значение Nothing** , если указан параметр **адексекутенорекордс** . в противном случае Execute возвращает закрытый **набор записей**.  
  
 Возвращаемый объект **набора записей** всегда является однонаправленным курсором только для чтения. Если требуется объект **набора записей** с дополнительными функциональными возможностями, сначала создайте объект **набора записей** с параметрами требуемого свойства, а затем используйте метод объекта набора **записей** [(ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) для выполнения запроса и возврата требуемого типа курсора.  
  
 Содержимое аргумента *CommandText* зависит от поставщика и может быть стандартным синтаксисом SQL или специальным форматом команды, поддерживаемым поставщиком.  
  
 Когда эта операция завершается, будет выдано событие Ексекутекомплете.  
  
> [!NOTE]
>  URL-адреса, использующие схему HTTP, автоматически вызывают [поставщик OLE DB Майкрософт для публикации в Интернете](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Дополнительные сведения см. в разделе [абсолютные и относительные URL-адреса](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
