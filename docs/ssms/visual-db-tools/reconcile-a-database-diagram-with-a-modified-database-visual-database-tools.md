---
title: Согласование диаграммы базы данных с измененной базой данных
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 247f8fe68dca157a98b9e0c0a36445422cc3332f
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999517"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a>Согласование диаграммы базы данных с измененной базой данных (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Сохраняйте диаграмму базы данных, когда вы готовы обновить базу данных для согласования с текущей диаграммой. Однако если с момента открытия базы данных другие пользователи внесли изменения в базу данных, то внесенные ими изменения могут повлиять на вашу диаграмму, и наоборот.  
  
Сохранение диаграммы приводит к согласованию базы данных с диаграммой путем перезаписи изменений, внесенных другими пользователями.  
  
### <a name="to-update-a-database-to-match-your-diagram"></a>Обновление базы данных для согласования с диаграммой  
  
1.  Сохраните диаграмму базы данных.  
  
    Если диаграмма до этого не сохранялась, введите ее имя в диалоговом окне **Сохранение новой диаграммы базы данных** и нажмите кнопку **ОК**.  
  
2.  В диалоговом окне **Сохранение** перечислены таблицы, которые затронет сохранение диаграммы. Чтобы продолжить, нажмите кнопку **Да** .  
  
3.  В диалоговом окне **Обнаружены изменения базы данных** перечислены объекты, в которые были внесены изменения и которые будут исправлены для согласования с диаграммой. Нажмите кнопку **Да** для сохранения диаграммы и подтверждения всех изменений в списке.  
  
    > [!NOTE]  
    > Если в диаграмме содержатся удаленные из базы данных таблицы и столбцы, то при сохранении диаграммы в базе данных будут повторно созданы только их определения. При этом процессе не восстанавливаются данные, которые существовали в этих объектах до их удаления.  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a>Обновление диаграммы для согласования с измененной базой данных  
  
1.  Закройте диаграмму без сохранения изменений.  
  
2.  Щелкните диаграмму правой кнопкой мыши в обозревателе объектов.  
  
3.  В контекстном меню выберите пункт **Обновить**.  
  
4.  Снова откройте диаграмму.  
  
## <a name="see-also"></a>См. также:  
[Работа с диаграммами баз данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  
