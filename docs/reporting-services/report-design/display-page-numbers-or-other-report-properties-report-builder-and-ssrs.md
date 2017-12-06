---
title: "Отображение номеров страниц или других свойств отчета (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7d95245-4709-4d04-acb4-59bf71e60d97
caps.latest.revision: "7"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: e577222bf9a1366830e75708730198920985872d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="display-page-numbers-or-other-report-properties-report-builder-and-ssrs"></a>Отображение номеров страниц или других свойств отчета (построитель отчетов и службы SSRS)
  К верхним или нижним колонтитулам страниц в отчете легко добавить номера страниц, заголовок отчета, имя файла и другие свойства отчета. Эти свойства хранятся в виде полей в папке «Встроенные поля» в области данных отчета.  
  
-   Время выполнения;  
  
-   Номер страницы;  
  
-   Папка отчета;  
  
-   Имя отчета  
  
-   URL-адрес сервера отчетов;  
  
-   Всего страниц  
  
-   Идентификатор пользователя  
  
-   Язык  
  
 При задании номера страницы может понадобиться добавить слово «Страница» перед номером. Также можно отобразить общее число страниц.  
  
> [!NOTE]  
>  Добавление общего числа страниц в нижний колонтитул может снизить производительность во время выполнения или предварительного просмотра отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-page-number-or-other-report-properties"></a>Добавление номера страницы или других свойств отчета  
  
1.  В области данных отчета разверните папку «Встроенные поля».  
  
    > [!NOTE]  
    >  Если область данных отчета не видна, на вкладке "Вид" установите флажок **Данные отчета**.  
  
2.  Перетащите поле **Номер страницы** из области данных отчета в верхний или нижний колонтитул отчета.  
  
    > [!NOTE]  
    >  Нижний колонтитул страницы добавляется в отчет автоматически. Чтобы добавить верхний колонтитул страницы, на вкладке **Вставка** выберите **Верхний колонтитул**, а затем **Добавить верхний колонтитул**.  
    >   
    >  Добавится текстовое поле, содержащее простое выражение [&PageNumber].  
  
### <a name="to-add-the-word-page-before-the-page-number"></a>Добавление слова «Страница» перед номером страницы  
  
1.  Щелкните правой кнопкой мыши текстовое поле, содержащее выражение [&PageNumber], и выберите пункт **Выражения**.  
  
     Текстовое поле **Задать выражение для: значение** содержит выражение =Globals!PageNumber.  
  
2.  Установите курсор после знака = и введите текст **"Page " &**.  
  
     Теперь выражение будет иметь вид ="Стр. "&Globals!PageNumber  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-total-number-of-pages-after-the-page-number"></a>Добавление общего числа страниц после номера страницы  
  
1.  Щелкните правой кнопкой мыши текстовое поле с выражением и выберите пункт **Выражения**.  
  
2.  Введите текст **&" из "&** в конце выражения.  
  
3.  На панели категорий разверните узел **Встроенные поля** и дважды щелкните поле **TotalPages**.  
  
     Выражение будет иметь вид ="Стр. "&Globals!PageNumber &" из "&Globals!TotalPages  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Верхние и нижние колонтитулы страницы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md)   
 [Форматирование текста в текстовом поле (построитель отчетов и службы SSRS)](../../reporting-services/report-design/format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
  
