---
title: "Просмотр отчетов тестовый случай (SybaseToSQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Test Case Reports
ms.assetid: cb75d281-43ef-4f4a-b754-2c4ee3b62ae7
caps.latest.revision: 5
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6ac96a35ea5f97ef58be45b2fbd2a04980f8b4cb
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="viewing-test-case-reports-sybasetosql"></a>Просмотр отчетов тестовый случай (SybaseToSQL)
В отчете тестовый случай отображаются результаты проверки и тестирования Общие сведения. В случае сбоя теста также отображаются сведения об все несоответствующие данные в проверенный объектов.  
  
## <a name="report-structure"></a>Структура отчета  
Верхней части отчета показаны эти статистические данные:  
  
-   Общее число объектов протестированных и количество объектов, для которых проверка выполнена успешно.  
  
-   Общее число проверенных таблиц и внешних ключей и количество таблиц и внешние ключи, которые успешно совпадают.  
  
-   Время начала, время окончания тестового случая и общее время, затраченное на выполнение.  
  
Оставшаяся часть отчета показывает сведения в четырех категорий:  
  
**Необходимые условия ошибок**  
Показывает все ошибки, появившиеся в **необходимые компоненты** шаг. Как правило он пропускается.  
  
**Инициализация**  
Показывает состояние выполнения как **успех** или **сбоя**.  
  
**Объекты результатов теста**  
Сравнение результатов (успех или сбой) и несоответствий, которые SSMA тестировщик обнаружил в случае сбоя.  
  
**Завершение**  
Показывает состояние выполнения как **успех** или **сбоя**.  
  
## <a name="see-also"></a>См. также:  
[Выполнение тестовых случаев &#40; SybaseToSQL &#41;](../../ssma/sybase/running-test-cases-sybasetosql.md)  
[Тестирование миграции объектов базы данных &#40; SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  

