---
title: Создание инструкции SQL (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
ms.assetid: 0acc71e2-8004-4dd8-8592-05c022bdd692
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 96e3c04692360bd13010fe40063b0e761d60b2ce
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73779977"
---
# <a name="constructing-an-sql-statement-odbc"></a>Конструирование инструкций SQL (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Приложения ODBC почти всегда осуществляют доступ к базе данных, выполняя инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Формат инструкций зависит от требования приложения. Инструкции SQL можно создавать следующими способами.  
  
-   Жестко запрограммированные  
  
     Статические инструкции, которые приложение выполняет в виде фиксированной задачи.  
  
-   Сформированные во время выполнения  
  
     Инструкции SQL, сформированные во время выполнения, дают возможность пользователю приспосабливать инструкцию, используя широко распространенные предложения, например SELECT, WHERE и ORDER BY. Это включает нерегламентированные запросы, вводимые пользователем.  
  
 Драйвер ODBC для клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] анализирует инструкции SQL только для синтаксиса ODBC и ISO, который не поддерживается непосредственно [!INCLUDE[ssDE](../../includes/ssde-md.md)], который преобразуется в [!INCLUDE[tsql](../../includes/tsql-md.md)]. Все остальные синтаксисы SQL передаются в [!INCLUDE[ssDE](../../includes/ssde-md.md)] без изменений, где [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определит, является ли он допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Такой подход имеет следующие два преимущества.  
  
-   Сокращение издержек  
  
     Издержки при обработке сведены к минимуму, поскольку драйверу приходится просматривать лишь небольшой набор предложений ODBC и ISO.  
  
-   Гибкость  
  
     Программисты могут адаптировать переносимость своих приложений. Чтобы расширить переносимость для различных баз данных, используется прежде всего синтаксис ODBC и ISO. Для расширений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется соответствующий синтаксис [!INCLUDE[tsql](../../includes/tsql-md.md)]. Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает полный синтаксис [!INCLUDE[tsql](../../includes/tsql-md.md)] поэтому приложения на основе ODBC могут использовать все функции в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список столбцов в инструкции SELECT должен содержать только столбцы, необходимые для выполнения текущей задачи. Это не только сокращает объем данных, отправляемых по сети, но и снижает эффект изменений в базе данных на приложение. Если приложение не ссылается на столбец в таблице, то оно не затрагивается никакими изменениями, сделанными в этом столбце.  
  
## <a name="see-also"></a>См. также раздел  
 [Выполняя запросы &#40;ODBC&#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
