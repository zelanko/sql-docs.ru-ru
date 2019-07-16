---
title: Конструирование инструкций SQL (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: fa955f31d26c87b39585ddead6bc5899a9e00679
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206780"
---
# <a name="constructing-an-sql-statement-odbc"></a>Конструирование инструкций SQL (ODBC)
  Приложения ODBC почти всегда осуществляют доступ к базе данных, выполняя инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)]. Формат инструкций зависит от требования приложения. Инструкции SQL можно создавать следующими способами.  
  
-   Жестко запрограммированные  
  
     Статические инструкции, которые приложение выполняет в виде фиксированной задачи.  
  
-   Сформированные во время выполнения  
  
     Инструкции SQL, сформированные во время выполнения, дают возможность пользователю приспосабливать инструкцию, используя широко распространенные предложения, например SELECT, WHERE и ORDER BY. Это включает нерегламентированные запросы, вводимые пользователем.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC клиента выполняет синтаксический анализ инструкции SQL только для синтаксиса ODBC и ISO, не поддерживаемого непосредственно компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], который драйвер преобразует в [!INCLUDE[tsql](../../includes/tsql-md.md)]. Весь остальной синтаксис SQL передается [!INCLUDE[ssDE](../../includes/ssde-md.md)] без изменений, где [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определить, является ли допустимым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Такой подход имеет следующие два преимущества.  
  
-   Сокращение издержек  
  
     Издержки при обработке сведены к минимуму, поскольку драйверу приходится просматривать лишь небольшой набор предложений ODBC и ISO.  
  
-   Гибкость  
  
     Программисты могут адаптировать переносимость своих приложений. Чтобы расширить переносимость для различных баз данных, используется прежде всего синтаксис ODBC и ISO. Для расширений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется соответствующий синтаксис [!INCLUDE[tsql](../../includes/tsql-md.md)]. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC для собственного клиента поддерживает полную [!INCLUDE[tsql](../../includes/tsql-md.md)] синтаксис, поэтому приложения на основе ODBC можно воспользоваться преимуществами всех функций в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Список столбцов в инструкции SELECT должен содержать только столбцы, необходимые для выполнения текущей задачи. Это не только сокращает объем данных, отправляемых по сети, но и снижает эффект изменений в базе данных на приложение. Если приложение не ссылается на столбец в таблице, то оно не затрагивается никакими изменениями, сделанными в этом столбце.  
  
## <a name="see-also"></a>См. также  
 [Выполнение запросов &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
