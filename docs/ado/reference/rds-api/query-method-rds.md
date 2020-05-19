---
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
ms.openlocfilehash: b3025f37b47cd545e7e7cde127e96740077ab961
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82751499"
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
  
 *Подключение*  
 **Строковое** значение, содержащее сведения о соединении с сервером. Это похоже на свойство [Connect](../../../ado/reference/rds-api/connect-property-rds.md) .  
  
 *Запрос*  
 **Строка** , содержащая SQL-запрос.  
  
## <a name="remarks"></a>Примечания  
 В запросе должен использоваться диалект SQL сервера базы данных. Если с выполненным запросом возникла ошибка, возвращается состояние результата. Метод **Query** не выполняет проверку синтаксиса строки **запроса** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект DataFactory (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры объекта DataFactory, а также методов Query и CreateObject (VBScript)](../../../ado/reference/rds-api/datafactory-object-query-method-and-createobject-method-example-vbscript.md)


