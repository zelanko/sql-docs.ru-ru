---
title: Диалоговое окно свойств набора данных, поля (построитель отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6f79a72033039babf117d69330e452ffc47d75b1
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56298097"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a>Диалоговое окно «Свойства набора данных» — «Поля» (построитель отчетов)
  Чтобы изменить коллекцию полей для набора данных отчета, перейдите на вкладку **Поля** в диалоговом окне **Свойства набора данных** . Список полей формируется автоматически, но с помощью вкладки **Поля** можно добавлять, изменять и удалять поля запросов и вычисляемые поля.  
  
 Вычисляемые поля поддерживаются только во внедренных наборах данных. Дополнительные сведения см. в разделе [Внедренные и общие наборы данных отчета (построитель отчетов и службы SSRS)](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Параметры  
 **Добавить**  
 Добавить в набор данных новое поле запроса или вычисляемое поле.  
  
 **Удаление**  
 Удалить выбранное поле из набора данных.  
  
 **Имя поля**  
 Введите имя для поля. Имя поля должно быть уникально в пределах набора данных. Имя каждого существующего поля в наборе данных заполняется заранее.  
  
 **Источник поля**  
 Введите значение для поля.  
  
 Для вычисляемого поля источник должен иметь имя существующего поля, возвращаемого запросом набора данных, или имя выражения, создаваемого пользователем. Например, чтобы создать поле, представляющее удесятеренное значение поля Sales в запросе, используйте выражение `=10 * Fields!Sales.Value`.  
  
 Для поля запроса источник должен иметь имя существующего поля, возвращаемого запросом набора данных.  
  
 **Выражение (fx)**  
 Создайте или измените выражение для нового вычисляемого поля. Эта кнопка появляется, только если нажать кнопку **Добавить** и выбрать пункт **Вычисляемое поле**.  
  
## <a name="see-also"></a>См. также  
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Создание общего или внедренного набора данных (построитель отчетов и службы SSRS)](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Справка построителя отчетов для диалоговых окон, панелей и мастеров](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Диалоговое окно свойств набора данных, параметры &#40;построитель отчетов&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md)   
 [Диалоговое окно свойств набора данных, фильтрует &#40;построитель отчетов&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md)   
 [Диалоговое окно свойств набора данных, параметры &#40;построитель отчетов&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md)   
 [Диалоговое окно свойств набора данных, запрос &#40;построитель отчетов&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [Выражения (построитель отчетов и службы SSRS)](report-design/expressions-report-builder-and-ssrs.md)   
 [Подключения к данным, источники данных и строки подключения в построителе отчетов](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
