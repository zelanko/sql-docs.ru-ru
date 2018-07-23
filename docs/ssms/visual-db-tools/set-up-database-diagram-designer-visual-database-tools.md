---
title: Настройка конструктора диаграмм баз данных (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54714f5d4c1cd0db5c9117e3812107caf039676e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37997666"
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>Настройка конструктора диаграмм баз данных (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Чтобы можно было использовать конструктор диаграмм баз данных, его вначале должен установить член роли **db_owner** для контроля доступа к диаграммам.  
  
### <a name="to-set-up-database-diagramming"></a>Настройка создания схем баз данных  
  
1.  Разверните узел базы данных в обозревателе объектов.  
  
2.  В окне подключения к базе данных разверните узел «Диаграммы баз данных».  
  
3.  Нажмите кнопку **Да** , когда получите подсказку о необходимости настроить создание диаграмм баз данных.  
  
    > [!NOTE]  
    > В базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] создаются таблица диаграмм базы данных, системные хранимые процедуры и системная функция.  
  
4.  Visual Studio создает следующие объекты в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
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
[Основные сведения о владении диаграммами баз данных (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[Обновление диаграмм баз данных из предыдущих версий (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](http://msdn.microsoft.com/en-us/8c805ae2-91ed-4133-96f6-9835c908f373)  
  
