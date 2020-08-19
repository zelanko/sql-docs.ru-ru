---
description: Метод Query (служба удаленных рабочих столов)
title: Метод query (RDS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
ms.openlocfilehash: b4d883d9498622c5118ecfcaa418bd734e4356c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438866"
---
# <a name="query-method-rds"></a>Метод Query (служба удаленных рабочих столов)
Использует допустимую строку SQL-запроса для возврата [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
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
 Объектная переменная, представляющая объект [RDSServer.](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) DataObject.  
  
 *Соединение*  
 **Строковое** значение, содержащее сведения о соединении с сервером. Это похоже на свойство [Connect](../../../ado/reference/rds-api/connect-property-rds.md) .  
  
 *Запрос*  
 **Строка** , содержащая SQL-запрос.  
  
## <a name="remarks"></a>Remarks  
 В запросе должен использоваться диалект SQL сервера базы данных. Если с выполненным запросом возникла ошибка, возвращается состояние результата. Метод **Query** не выполняет проверку синтаксиса строки **запроса** .  
  
## <a name="applies-to"></a>Применение  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


