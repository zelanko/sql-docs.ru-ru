---
title: Настройка конструктора диаграмм баз данных (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d71ea2d6a10755ef52e0cac37ddcd2385d82d9cb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067625"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Настройка конструктора диаграмм баз данных (визуальные инструменты для баз данных)
  Чтобы можно было использовать конструктор диаграмм баз данных, его вначале должен установить член роли **db_owner** для контроля доступа к диаграммам.  
  
### <a name="to-set-up-database-diagramming"></a>Настройка создания схем баз данных  
  
1.  Разверните узел базы данных в обозревателе объектов.  
  
2.  В окне подключения к базе данных разверните узел «Диаграммы баз данных».  
  
3.  Нажмите кнопку **Да** , когда получите подсказку о необходимости настроить создание диаграмм баз данных.  
  
    > [!NOTE]  
    >  В базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создаются таблица диаграмм базы данных, системные хранимые процедуры и системная функция.  
  
4.  Visual Studio создает следующие объекты в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    1.  таблица sysdiagrams;  
  
    2.  хранимая процедура sp_alterdiagram;  
  
    3.  хранимая процедура sp_creatediagram;  
  
    4.  хранимая процедура sp_dropdiagram;  
  
    5.  хранимая процедура sp_renamediagram;  
  
    6.  функция fn_diagramobjects;  
  
    7.  хранимая процедура sp_helpdiagrams;  
  
    8.  хранимая процедура sp_helpdiagramsdefinition;  
  
    9. хранимая процедура sp_upgraddiagrams.  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о владении диаграммами базы данных &#40;визуальные инструменты для баз данных&#41;](visual-database-tools.md)   
 [Обновление диаграмм баз данных из предыдущих выпусков &#40;визуальные инструменты для баз данных&#41;](upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)   
 [ALTER AUTHORIZATION (Transact-SQL)](/sql/t-sql/statements/alter-authorization-transact-sql)  
  
  
