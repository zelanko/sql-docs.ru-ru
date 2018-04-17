---
title: Формирование результата и освободить результат инструкции | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- result-generating statements [ODBC]
- batches [ODBC], result-generating statements
- batches [ODBC], result-free statements
- SQL statements [ODBC], batches
- result-free statements [ODBC]
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 373d1b2c3d850fd46352ca4dcbbd59a482b84ca2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="result-generating-and-result-free-statements"></a>Формирование результата и результат без инструкций
Инструкции SQL можно разделить на следующие пять категорий слабо:  
  
-   **Привести-формирования набора инструкций** это инструкций SQL, которые формируют результирующий набор. Например **ВЫБЕРИТЕ** инструкции.  
  
-   **Строки-формирования число инструкций** это инструкций SQL, которые создают количество затронутых строк. Например **обновление** или **удалить** инструкции.  
  
-   **Инструкции определения языка DDL данных** это инструкции SQL, изменение структуры базы данных. Например **CREATE TABLE** или **DROP INDEX**.  
  
-   **Изменение контекста инструкций** это инструкции SQL, изменяющие контекст базы данных. Например **используйте** и **ЗАДАТЬ** инструкций в SQL Server.  
  
-   **Административные инструкций** это инструкции SQL, используемые при выполнении административных задач в базе данных. Например **GRANT** и **ОТОЗВАТЬ**.  
  
 Инструкции SQL в первых двух категорий называются *формирование результата инструкции*. Инструкции SQL в последние три категории называются *освободить результат инструкции*. ODBC определяет семантику пакетов, которые включают в себя только создание результат инструкции. Эту семантику различаются и, следовательно, определяемые источником данных. Например драйвер SQL Server не поддерживает удаление объекта и ссылка на или повторное создание тот же объект в одном пакете. Таким образом, термин *пакета* как в это руководство относится только к результат формирования пакетов инструкций.
