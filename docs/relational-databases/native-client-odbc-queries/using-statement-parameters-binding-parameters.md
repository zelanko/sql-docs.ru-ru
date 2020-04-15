---
title: Связывание параметров Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 01e179d2abc6ef786f94b6d7938f0e21938c5a59
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304650"
---
# <a name="using-statement-parameters---binding-parameters"></a>Использование параметров инструкции — привязка параметров
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Каждый маркер параметра в инструкции SQL должен быть сопоставлен переменной в приложении (привязан к ней), прежде чем можно выполнить инструкцию. Это делается путем вызова функции [S'LBindParameter.](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) **S'LBindParameter** описывает переменную программы (адрес, тип данных C и т.д.) для водителя. Она также определяет маркер параметра, указывая его порядковое значение, а затем описывая характеристики представляемого им объекта SQL (тип данных SQL, точность и т. д.).  
  
 Маркеры параметров могут быть привязаны или повторно привязаны в любое время перед выполнением инструкции. Привязка параметра действует до тех пор, пока не происходит одно из следующих событий.  
  
-   Вызов на [s'LFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) с параметром *опциона,* установленным для SQL_RESET_PARAMS освобождает все параметры, связанные с ручкой оператора.  
  
-   Вызов на **S'LBindParameter** с *ParameterNumber,* установленным на облаве на маркер связанного параметра, автоматически выпускает предыдущую привязку.  
  
 Приложение также может привязать параметры к массивам переменных программы для пакетной обработки инструкции SQL. Существует два типа привязки массивов.  
  
-   Привязка на уровне столбца выполняется, если каждый отдельный параметр привязан к собственному массиву переменных.  
  
     Связывание по-колонке определяется, вызывая [S'LSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с *набором attribute,* чтобы SQL_ATTR_PARAM_BIND_TYPE и *ValuePtr* установлен SQL_PARAM_BIND_BY_COLUMN.  
  
-   Привязка на уровне строки выполняется, если все параметры в инструкции SQL привязаны в виде блока к массиву структур, которые содержат отдельные переменные для параметров.  
  
     Связывание по гребню определяется путем вызова **S'LSetStmtAttr** с *атрибутом,* установленным для SQL_ATTR_PARAM_BIND_TYPE и *ValuePtr,* установленным для размера структуры, удерживающей переменные программы.  
  
 Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] водитель Native Client ODBC отправляет на сервер параметры символов или параметра бинарной строки, он прикладывает значения к длине, указанной в параметре **колонки S'LBindParameter** *ColumnSize.* Если приложение ODBC 2.x определяет 0 для *ColumnSize,* драйвер приспобит значение параметра точностью типа данных. Точность равна 8000 при соединении с сервером [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и 255 при соединении с предыдущими версиями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *ColumnSize* находится в байтах для вариантов столбцов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает определение имен для параметров хранимых процедур. В ODBC 3.5 также появилась поддержка именованных параметров, используемых при вызове хранимых процедур [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта поддержка может использоваться для следующих действий.  
  
-   Вызов хранимой процедуры и предоставление значений для подмножества параметров, заданных для хранимой процедуры.  
  
-   Указание параметров в приложении не в той последовательности, в какой они были заданы при создании хранимой процедуры.  
  
 Именованные параметры поддерживаются [!INCLUDE[tsql](../../includes/tsql-md.md)] только при использовании выписки **EXECUTE** или последовательности побега ODBC CALL для выполнения сохраненной процедуры.  
  
 Если **SQL_DESC_NAME** установлен для параметра сохраненной процедуры, все сохраненные параметры процедуры в запросе также должны установить **SQL_DESC_NAME.**  Если буквальные значения используются в сохраненных вызовах процедуры, где параметры **SQL_DESC_NAME** установлены, то буквалы должны использовать*значение* *имени*=формата , где *имя* является именем параметра сохраненной процедуры (например, @p1). Для получения дополнительной [информации см.](https://go.microsoft.com/fwlink/?LinkId=167215)  
  
## <a name="see-also"></a>См. также:  
 [Использование параметров инструкции](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
