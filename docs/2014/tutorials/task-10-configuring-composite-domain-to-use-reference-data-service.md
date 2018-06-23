---
title: 'Задача 10: Настройка составного домена для использования службы ссылочных данных | Документы Microsoft'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 752eefde-8b87-4f54-878e-9963ccbadc8e
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 2a5d37578ac8336b67201161ef4de59baf90649c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098081"
---
# <a name="task-10-configuring-composite-domain-to-use-reference-data-service"></a>Задача 10. Настройка составного домена для использования службы ссылочных данных
  В этой задаче вы настраиваете **проверки адреса** составного домена для использования **Melissa Data — Address Check** службы. Во время выполнения при проведении очистки данных службы DQS передают значения доменов в домен проверки адреса, чтобы служба выполнила очистку данных. В разделе [карты домена или составного домена со ссылочными данными](http://msdn.microsoft.com/library/hh213030.aspx) для получения дополнительных сведений.  
  
1.  На главной странице **клиента DQS**, нажмите кнопку **Suppliers (Управление доменами)** под **Недавние базы знаний** для запуска **управления доменами**страницы.  
  
2.  Выберите **проверки адреса** составной домен в **список доменов**.  
  
3.  На правой панели переключитесь **ссылочных данных** вкладки.  
  
     ![Ссылки на вкладке данные](../../2014/tutorials/media/et-configuringcdtouserds-01.jpg "ссылаться вкладки \"данные\"")  
  
4.  Нажмите кнопку **Обзор** на панели инструментов.  
  
5.  На **каталог поставщиков ссылочных данных сети** выберите **флажок** рядом с **Melissa Data — Address Check**.  
  
     ![Выбрать Melissa Data — проверка адреса](../../2014/tutorials/media/et-configuringcdtouserds-02.jpg "выбрать Melissa Data — проверка адреса")  
  
6.  На панели справа в **схемы** сопоставьте **строка адреса** домена **Address Line (M)** элемента схемы с помощью раскрывающегося списка.  
  
     ![Сопоставление элемента схемы RDS с доменом](../../2014/tutorials/media/et-configuringcdtouserds-03.jpg "сопоставление элемента схемы RDS с доменом")  
  
7.  Нажмите кнопку **добавить элемент схемы (+)** на панели инструментов, чтобы создать запись в списке.  
  
     ![Добавление кнопки панели инструментов для записи схемы](../../2014/tutorials/media/et-configuringcdtouserds-04.jpg "схемы запись кнопка добавления панели инструментов")  
  
8.  Сопоставьте следующие домены DQS с помощью раскрывающегося списка, как показано на следующем рисунке.  
  
     ![Сопоставление элементов схемы RDS с доменами](../../2014/tutorials/media/et-configuringcdtouserds-05.jpg "сопоставление элементов схемы RDS с доменами")  
  
9. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 11. Публикация базы знаний](../../2014/tutorials/task-11-publishing-the-knowledge-base.md)  
  
  