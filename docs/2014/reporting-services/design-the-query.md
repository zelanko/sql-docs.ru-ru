---
title: Создание запроса | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.designquery.f1
ms.assetid: 2dad800f-10a1-453c-8761-2935b9826d84
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4ce60e8326149ac0d8e7f54a84dd344f5088ee3d
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56032622"
---
# <a name="design-the-query"></a>Создание запроса
  На этой странице мастера отчетов можно создать запрос: ввести его вручную, воспользоваться построителем запросов для интерактивного создания запроса или импортировать запрос из другого отчета.  
  
 Какие именно запросы могут быть введены на этой странице, зависит от выбора типа источника данных на странице «Выбор источника данных» (на предыдущей странице мастера отчетов). Например, если в качестве источника данных выбран [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], то допустим ввод инструкций [!INCLUDE[tsql](../includes/tsql-md.md)] или имен хранимых процедур. Если же в качестве источника данных выбраны службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], то панель запроса становится недоступной, а возможность прямого ввода запроса отключается. Задать запрос можно только при помощи построителя запросов.  
  
## <a name="options"></a>Параметры  
 **Строка запроса**  
 Введите запрос получения данных, которые будут использованы в отчете.  
  
 **Построитель запросов**  
 Нажмите кнопку **Построитель запросов** , чтобы открыть конструктор запросов применительно к источнику данных, либо импортировать запрос из другого отчета.  
  
 Дополнительные сведения о конструкторах запросов см. в разделе [Reporting Services Query Designers](../../2014/reporting-services/reporting-services-query-designers.md).  
  
## <a name="example"></a>Пример  
 Для типа источника данных **Microsoft SQL Server**, следующий запрос возвращает список фамилий из [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] базы данных `Person` таблицы.  
  
```  
SELECT LastName FROM Person.Person;  
```  
  
 Для типа источника данных **Microsoft SQL Server**, следующий запрос выполняет [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] хранимой процедуры `uspGetEmployeeManagers` применительно к служащему с идентификационным номером 1:  
  
```  
EXEC uspgetEmployeeManagers '1';  
```  
  
## <a name="see-also"></a>См. также  
 [Справка мастера отчетов](../../2014/reporting-services/report-wizard-help.md)   
 [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Добавление данных в отчет &#40;построитель отчетов и службы SSRS&#41;](report-data/report-datasets-ssrs.md)  
  
  
