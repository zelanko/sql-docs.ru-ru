---
title: Прямое исполнение Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a89888ac055e83ab38588646f2f9b38ecd6444d0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297999"
---
# <a name="direct-execution"></a>Прямое выполнение
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Прямое выполнение — это наиболее распространенный способ выполнения инструкции. Приложение создает строку символов, содержащую [!INCLUDE[tsql](../../../includes/tsql-md.md)] оператора, и отправляет ее для выполнения с помощью функции **SLExecDirect.** Когда инструкция достигает сервера, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] компилирует ее в план выполнения и немедленно запускает план.  
  
 Прямое выполнение обычно используется приложениями, которые создают и выполняют инструкции во время выполнения, и является наиболее эффективным методом для инструкций, которые будут выполняться одновременно. Недостатком многих баз данных является то, что SQL-инструкция должна анализироваться и компилироваться при каждом выполнении, что увеличивает нагрузку при неоднократном использовании данной процедуры.  
  
 В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] значительно повышена производительность прямого выполнения часто выполняемых инструкций в многопользовательских средах, а использование SQLExecDirect с маркерами параметров для часто используемых инструкций SQL может приблизить их эффективность к эффективности выполнения после подготовки.  
  
 При подключении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляру драйвер Native Client ODBC использует [sp_executesql](../../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md) для передачи выписки или партии, указанной в **S'LExecDirect.** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]логика быстрого определения того, соответствует ли выписка или пакет, выполняемый **с sp_executesql,** выписке или пакету, генерируемому планом выполнения, который уже существует в памяти. В случае совпадения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] повторно использует существующий план, а не компилирует новый. Это означает, что обычно выполняемые операторы S'L, выполняемые с **помощью S'LExecDirect** в системе с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]большим количеством пользователей, получат преимущества для повторного использования, которые были доступны только для сохраненных процедур в более ранних версиях .  
  
 Данное преимущество работает только в случае одновременного выполнения одной инструкции или пакета SQL несколькими пользователями. Следуйте этим соглашениям по написанию кода для повышения вероятности того, что инструкции SQL, выполняемые различными клиентами, будут достаточно похожи, чтобы повторно использовать планы выполнения.  
  
-   Не включайте константы данных в инструкции SQL. Вместо этого используйте маркеры параметров, привязанные к переменным программы. Для получения дополнительной [информации см.](../../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
-   Используйте полные имена объектов. Планы выполнения не будут использоваться повторно при неполных именах объектов.  
  
-   Соединения приложения по возможности должны использовать стандартный набор параметров соединений и инструкций. Планы выполнения, созданные для соединения с одним набором параметров (например ANSI_NULLS), не используются для соединения, имеющего другой набор параметров. Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] имеют одинаковые установки по умолчанию для этих параметров.  
  
 Если все операторы, выполняемые с **помощью** этих [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] конвенций, закодированы с помощью этих конвенций, при возникновении такой возможности можно повторно использовать планы выполнения.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение заявлений &#40;&#41;ODBC](../../../relational-databases/native-client-odbc-queries/executing-statements/executing-statements-odbc.md)  
  
  
