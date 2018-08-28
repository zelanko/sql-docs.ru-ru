---
title: Окно "Пространственные результаты" | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9fa7124b265912120d4fb17bf0dda993deeb49b2
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43061505"
---
# <a name="spatial-results-window"></a>Окно «Пространственные результаты»
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Окно **Пространственные результаты** содержит визуальные средства сопоставления для просмотра пространственных данных. Чтобы использовать окно «Пространственные результаты», результаты запроса должны содержать по крайней мере один пространственный столбец с данными геометрического или географического типа.  
  
> [!NOTE]  
>  Окно **Пространственные результаты** доступно только в случае, если результаты возвращаются в сетку в окне **Результаты** . Если для результатов задано возвращение в виде текста, это окно будет недоступно.  
  
## <a name="options"></a>Параметры  
 **Выберите пространственный столбец**  
 Укажите пространственный столбец для просмотра из числа пространственных столбцов в результатах запроса. В один момент времени можно выбрать только один столбец.  
  
 **Выберите столбец меток**  
 Укажите непространственный столбец из числа столбцов, возвращаемых в результатах запроса, чтобы задать метки для пространственных данных. В один момент времени можно выбрать только один столбец.  
  
 Этот параметр недоступен, если в запросе возвращаются только объекты Point.  
  
 **Выберите проекцию**  
 Географические данные отображаются в одной из четырех проекций: равноугольная проекция, проекция Меркатора, проекция Робинзона или проекция Бонна.  
  
 Этот параметр недоступен для геометрических данных.  
  
 **Масштаб**  
 Регулирует отображение карты по экспоненциальной шкале.  
  
 **Отобразить линии сетки**  
 Включает или выключает линии координатной сетки.  
  
 Для фигур-многоугольников метка будет отображаться только в случае, если фигура достаточно велика, чтобы вместить текст метки. Чтобы показать метки для маленьких фигур, увеличьте масштаб.  
  
> [!NOTE]  
>  Для экземпляров Point нельзя задавать метки.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр пространственных данных в обозревателе объектов](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [Пространственные данные (SQL Server)](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Редактор запросов компонента Database Engine (среда SQL Server Management Studio)](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Редакторы запросов и текста (SQL Server Management Studio)](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
