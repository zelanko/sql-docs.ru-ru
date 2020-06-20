---
title: Использование координатор распределенных транзакций Майкрософт (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a938b49a5497aa81b48cb4032286e9d748acceb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048134"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Использование координатора распределенных транзакции Майкрософт (ODBC)
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>Обновление двух и более экземпляров SQL Server с помощью координатора распределенных транзакций (MS DTC)  
  
1.  Подключитесь к координатору распределенных транзакций (MS DTC), используя функцию DtcGetTransactionManager MS DTC OLE. Дополнительные сведения о координаторе распределенных транзакций (MS DTC) см. в разделе «Координатор распределенных транзакций (Майкрософт)».  
  
2.  Вызывайте SQL Дриверконнект один раз для каждого устанавливаемого соединения Microsoft SQL Server.  
  
3.  Вызовите функцию MS DTC OLE ITransactionDispenser::BeginTransaction, чтобы начать транзакцию координатора распределенных транзакций (MS DTC) и получить объект Transaction, представляющий транзакцию.  
  
4.  Вызовите функцию [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) один или несколько раз для каждого из соединений ODBC, которые необходимо прикрепить к транзакции MS DTC. Второй параметр [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) должен иметь значение SQL_ATTR_ENLIST_IN_DTC, а третий параметр должен быть объектом Transaction (полученным на шаге 3).  
  
5.  Вызовите [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) по одному разу для каждого экземпляра SQL Server, который нужно обновить.  
  
6.  Вызовите функцию MS DTC OLE ITransaction::Commit, чтобы зафиксировать транзакцию MS DTC. Объект Transaction более не действителен.  
  
 Чтобы выполнить ряд транзакций MS DTC, повторите шаги с 3 по 6.  
  
 Чтобы освободить ссылку на объект Transaction, вызовите функцию MS DTC OLE ITransaction::Return.  
  
 Чтобы использовать соединение ODBC с транзакцией распределенного координатора транзакций (MS DTC), а затем использовать то же соединение с транзакцией локального SQL Server, вызовите функцию [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с параметром SQL_DTC_DONE.  
  
> [!NOTE]  
>  Можно также вызывать [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) и [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) по очереди для каждого экземпляра SQL Server, а не вызывать их описанным выше в шагах 4 и 5 способом.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение транзакций &#40;ODBC&#41;](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
