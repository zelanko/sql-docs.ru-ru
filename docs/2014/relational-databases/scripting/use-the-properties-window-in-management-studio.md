---
title: Использование окна "Свойства" в среде Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- viewing properties
- Properties window [SQL Server Management Studio]
- complex properties [SQL Server Management Studio]
ms.assetid: 903d4aca-f57c-43d9-a893-702eceaa7004
caps.latest.revision: 23
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b1c8a14431ed10908daabf3688a5869ee151f790
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099743"
---
# <a name="use-the-properties-window-in-management-studio"></a>Использование окна «Свойства» в среде Management Studio
  Окно свойств описывает состояние элемента в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], например соединение или оператор Showplan, и сведения об объектах базы данных, таких как таблицы, представления и конструкторы.  
  
 Окно свойств можно использовать для просмотра свойств текущего соединения. Многие свойства в окне свойств доступны только для чтения, однако могут быть изменены другими средствами среды [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Например, свойство «База данных» запроса в окне свойств доступно только для чтения, но может изменяться на панели инструментов.  
  
### <a name="to-view-properties-using-the-properties-window"></a>Просмотр свойств с помощью окна свойств  
  
1.  Если окна свойств нет на экране, выберите **Окно "Свойства"** в меню **Вид** или нажмите клавишу F4.  
  
2.  Выберите объект, который необходимо просмотреть.  
  
3.  Найдите в окне свойств соответствующее свойство.  
  
### <a name="to-view-connection-properties-of-a-query-window"></a>Просмотр свойств соединения окна запроса  
  
1.  Если окна свойств нет на экране, выберите **Окно "Свойства"** в меню **Вид** или нажмите клавишу F4.  
  
2.  В окне свойств можно увидеть все свойства соединения.  
  
### <a name="to-view-the-properties-of-a-showplan-operator"></a>Просмотр свойств инструкции оператора Showplan  
  
1.  В меню **Запрос** выберите пункт **Включить действительный план выполнения**.  
  
2.  В редакторе SQL-запросов введите текст запроса и выполните его.  
  
3.  Если окна свойств нет на экране, выберите **Окно "Свойства"** в меню **Вид** или нажмите клавишу F4.  
  
4.  На вкладке **План выполнения** редактора SQL-запросов нажмите значки инструкций для просмотра сведений об инструкциях в окне свойств.  
  
## <a name="see-also"></a>См. также  
 [Окно "Свойства" (среда Management Studio)](../../ssms/properties-window-management-studio.md)  
  
  