---
title: Занятие 9. Сборка и запуск приложения | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f52d3f3a-0b09-4b34-9112-0b3655271587
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: fdb619e98fe28742ac6b96acc6419513addfae25
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096359"
---
# <a name="lesson-9-build-and-run-the-application"></a>Lesson 9: Build and Run the Application
  После создания фильтра данных для таблицы данных далее необходимо построить и запустить приложение веб-сайта.  
  
### <a name="to-build-and-run-the-application"></a>Построение и запуск приложения  
  
1.  Нажмите клавиши **CTRL+F5** , чтобы запустить страницу Default.aspx без отладки, или нажмите клавишу F5, чтобы запустить эту страницу с отладкой.  
  
     В рамках процесса сборки происходит компиляция отчета, и все обнаруженные ошибки (такие как синтаксические ошибки в выражениях, используемых в отчете) добавляются к **списку задач** , находящемуся в нижней части окна Visual Studio.  
  
     Веб-страница откроется в браузере. В отчете отображается элемент управления ReportViewer. Для просмотра отчета, изменения масштаба и экспорта отчета в Excel можно использовать панель инструментов.  
  
2.  Наведите курсор мыши на любую строку в столбце **Имя** . Курсор мыши примет форму руки.  
  
3.  Щелкните любое значение в столбце **Имя** . Будет показан дочерний отчет с соответствующими отфильтрованными данными.  
  
4.  Щелкните значок **Возврат к родительскому отчету**на панели инструментов **ReportViewer** , чтобы перейти к **родительскому** отчету.  
  
     ![Детализация SSRS с помощью ReportViewer](../../2014/tutorials/media/ssrs-drillthrough-report.png "ssrs детализации с помощью ReportViewer")  
  
5.  Закройте браузер, чтобы выйти из приложения.  
  
  