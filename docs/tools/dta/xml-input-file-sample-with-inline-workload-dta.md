---
title: Образец входного файла XML со встроенной рабочей нагрузкой
description: В этой статье показан образец входного файла XML со встроенной рабочей нагрузкой, предназначенный для настройки рабочих нагрузок с помощью помощника по настройке ядра СУБД.
titleSuffix: DTA
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: 277b2d69ff796f3082d390a73e851199ef286efa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85731950"
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a>Образец входного XML-файла с описанием встроенной рабочей нагрузки (DTA)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Скопируйте и вставьте этот входной XML-файл, задающий рабочую нагрузку элементом **EventString** , в свой привычный редактор XML или текстовый редактор. Элемент **EventString** можно использовать для указания во входном файле XML рабочей нагрузки из скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] вместо использования отдельного файла рабочей нагрузки. Скопировав данный образец, замените значения, указанные для элементов **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**и **TuningOptions** , значениями, характерными для вашего сеанса настройки. Дополнительные сведения обо всех атрибутах и дочерних элементах, которые могут использоваться с этими элементами, см. в разделе [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md). В следующем образце используется только подмножество доступных атрибутов и параметров дочерних элементов.

## <a name="code"></a>Код

[!code-xml[InputFileSamples#InlineWorkloadInputFile](../../tools/dta/codesnippet/xml/xml-input-file-sample-wi_1.xml)]

## <a name="comments"></a>Комментарии

`USE database_name` EventString **EventString** .

## <a name="see-also"></a>См. также:

- [Запуск и использование помощника по настройке ядра СУБД](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)
- [Просмотр и работа с выходными данными помощника по настройке ядра СУБД](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)
- [Справочник по входным XML-файлам (помощник по настройке ядра СУБД)](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)