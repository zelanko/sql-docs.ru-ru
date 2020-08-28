---
description: Метод Query (служба удаленных рабочих столов)
title: Метод query (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Query method [ADO]
ms.assetid: 20f2480f-3758-405d-a379-05a0dce74796
author: rothja
ms.author: jroth
ms.openlocfilehash: 16220bf51fceb83cf22abb2779ad8a5804af4326
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981855"
---
# <a name="query-method-rds"></a>Метод Query (служба удаленных рабочих столов)
Использует допустимую строку SQL-запроса для возврата [набора записей](../ado-api/recordset-object-ado.md).  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
Set Recordset = DataFactory.Query(Connection, Query)  
```  
  
#### <a name="parameters"></a>Параметры  
 *набор записей*  
 Объектная переменная, представляющая объект **набора записей** .  
  
 *DataFactory*  
 Объектная переменная, представляющая объект [RDSServer.](./datafactory-object-rdsserver.md) DataObject.  
  
 *Соединение*  
 **Строковое** значение, содержащее сведения о соединении с сервером. Это похоже на свойство [Connect](./connect-property-rds.md) .  
  
 *Запрос*  
 **Строка** , содержащая SQL-запрос.  
  
## <a name="remarks"></a>Remarks  
 В запросе должен использоваться диалект SQL сервера базы данных. Если с выполненным запросом возникла ошибка, возвращается состояние результата. Метод **Query** не выполняет проверку синтаксиса строки **запроса** .  
  
## <a name="applies-to"></a>Применение  
 [Объект DataFactory (RDSServer)](./datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](./datafactory-object-query-method-and-createobject-method-example-vbscript.md)