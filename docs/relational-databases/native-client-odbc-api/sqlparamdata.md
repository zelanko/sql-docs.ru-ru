---
title: СЗЛПарамДата (англ.) Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7a2cc7bfdf35bf30a0883eecf6767e03b6805253
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289088"
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Когда S'LParamData возвращает *ValuePtrPtr,* связанный с параметром, оцененным таблицей, приложение должно вызывать S'LPutData с *StrLen_Or_Ind.* Если *StrLen_Or_Ind* имеет значение больше 0, это означает, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] что приложение готово для Native Client для сбора данных параметров для следующей строки параметров, оцениваемой таблицей. Если *StrLen_Or_Ind* имеет значение 0, это означает, что для параметра, оцениваемого таблицей, больше нет строк данных. Для получения дополнительной информации [см. Связывание и передача данных параметрами и значениями столбца, оцениваемых таблицей.](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [СЗЛПарамДата](https://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
