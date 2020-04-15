---
title: Использование параметров выписки Документы Майкрософт
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
- ODBC, parameters
- statements [ODBC], parameters
- parameter markers [ODBC]
- SQL Server Native Client ODBC driver, statements
- ODBC applications, statements
ms.assetid: 2427d886-ec6c-49d7-b0b6-0d998b64cdb9
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 74cd70bcd9107d68551dc3f82eb1e01f76a549b4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297906"
---
# <a name="using-statement-parameters"></a>Использование параметров инструкции
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Параметр — это переменная в инструкции SQL, позволяющая в приложении ODBC осуществлять следующее.  
  
-   Эффективно передавать значения для столбцов таблицы.  
  
-   Повышать степень взаимодействия с пользователем при конструировании критериев запроса.  
  
-   Управление **текстом,** **ntext,** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]и данными **изображения** и -специфические типы данных C.  
  
 Например, таблица **части** имеет столбцы под названием **PartID,** **Описание**и **Цена**. Для добавления компонента без параметров необходимо составить инструкцию SQL, например:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 Эта инструкция вполне подходит для вставки одной строки с заранее известным набором значений, но если в приложении необходимо вставить несколько строк, она становится менее приемлемой. Поэтому в ODBC разрешается заменять в приложении любое значение данных в инструкции SQL маркером параметра. Он обозначается вопросительным знаком (?). В следующем примере маркерами параметров заменены три значения данных.  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 Затем происходит привязка маркеров параметров к переменным приложения. Для вставки новой строки в приложении достаточно только задать значения параметров и выполнить инструкцию. После этого драйвер получает текущие значения переменных и передает их в источник данных. Если инструкция выполняется неоднократно, то в приложении можно дополнительно оптимизировать этот процесс с помощью подготовки инструкции.  
  
 Ссылка на каждый маркер параметра осуществляется по порядковому номеру; параметры нумеруются слева направо. Первый слева параметр в инструкции SQL имеет порядковый номер 1; следующий — 2 и т. д.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Привязка параметров](../../relational-databases/native-client-odbc-queries/using-statement-parameters-binding-parameters.md)  
  
## <a name="see-also"></a>См. также:  
 [Выполнение запросов &#40;&#41;ODBC](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
