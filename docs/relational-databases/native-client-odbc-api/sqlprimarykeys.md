---
title: СЗЛPrimaryKeys Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2695d253030f13f71785046a25997ec6ee768622
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289060"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Таблица может иметь столбцы или столбцы, которые могут служить в качестве уникальных идентификаторов строк, а таблицы, созданные без ограничения PRIMARY KEY, возвращают пустой результат, установленный в S'LPrimaryKeys. Функция ODBC [S'LSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md) сообщает о кандидатах идентификаторов строк для таблиц без первичных ключей.  
  
 SLPrimaryKeys возвращается SQL_SUCCESS, существуют ли значения для параметров *CatalogName,* *SchemaName*или *TableName.* Функция SQLFetch возвращает значение SQL_NO_DATA, если в этих параметрах заданы недопустимые значения.  
  
 SLPrimaryKeys может быть выполнен анамнезным курсором сервера. Попытка выполнить s'LPrimaryKeys на курсоре updatable (динамическом или клавиатурном) вернет SQL_SUCCESS_WITH_INFO, указывающий на изменение типа курсора.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметре *CatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>Функция SQLPrimaryKeys и возвращающие табличные значения параметры  
 Если атрибут оператора SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE_TYPE, а не значение SQL_SS_NAME_SCOPE_TABLE по умолчанию, S'LPrimaryKeys вернет информацию о основных ключевых столбцах типов таблиц. Для получения более подробной информации о SQL_SOPT_SS_NAME_SCOPE, [см.](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Функция S'LPrimaryKeys](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
