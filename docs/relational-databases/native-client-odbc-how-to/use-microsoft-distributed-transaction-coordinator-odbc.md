---
title: "Используйте Microsoft координатор распределенных транзакций (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
caps.latest.revision: "12"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b8cb0ba58e3d85c28f5aeb056f6b4438533421c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Использование координатора распределенных транзакции Майкрософт (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>Обновление двух и более экземпляров SQL Server с помощью координатора распределенных транзакций (MS DTC)  
  
1.  Подключитесь к координатору распределенных транзакций (MS DTC), используя функцию DtcGetTransactionManager MS DTC OLE. Дополнительные сведения о координаторе распределенных транзакций (MS DTC) см. в разделе «Координатор распределенных транзакций (Майкрософт)».  
  
2.  Вызовите метод SQL DriverConnect по одному разу для каждого устанавливаемого соединения с Microsoft® SQL Server™.  
  
3.  Вызовите функцию MS DTC OLE ITransactionDispenser::BeginTransaction, чтобы начать транзакцию координатора распределенных транзакций (MS DTC) и получить объект Transaction, представляющий транзакцию.  
  
4.  Вызовите функцию [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) один или несколько раз для каждого из соединений ODBC, которые необходимо прикрепить к транзакции MS DTC. Второй параметр [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) должен иметь значение SQL_ATTR_ENLIST_IN_DTC, а третий параметр должен быть объектом Transaction (полученным на шаге 3).  
  
5.  Вызовите [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) по одному разу для каждого экземпляра SQL Server, который нужно обновить.  
  
6.  Вызовите функцию MS DTC OLE ITransaction::Commit, чтобы зафиксировать транзакцию MS DTC. Объект Transaction более не действителен.  
  
 Чтобы выполнить ряд транзакций MS DTC, повторите шаги с 3 по 6.  
  
 Чтобы освободить ссылку на объект Transaction, вызовите функцию MS DTC OLE ITransaction::Return.  
  
 Чтобы использовать соединение ODBC с транзакцией распределенного координатора транзакций (MS DTC), а затем использовать то же соединение с транзакцией локального SQL Server, вызовите функцию [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) с параметром SQL_DTC_DONE.  
  
> [!NOTE]  
>  Можно также вызывать [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) и [SQLExecDirect](http://go.microsoft.com/fwlink/?LinkId=58399) по очереди для каждого экземпляра SQL Server, а не вызывать их описанным выше в шагах 4 и 5 способом.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение транзакций &#40; ODBC &#41;](http://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
  
