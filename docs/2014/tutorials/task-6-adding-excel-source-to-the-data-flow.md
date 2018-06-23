---
title: 'Задача 6: Добавление источника Excel в поток данных | Документы Microsoft'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- data-quality-services
- integration-services
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0209055e-cb6b-4a07-909e-836596727a2c
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1cde5dc49851e7d8c808d4a6273f4d4caf6603e2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195707"
---
# <a name="task-6-adding-excel-source-to-the-data-flow"></a>Задача 6. Добавление источника Excel в поток данных
  В этой задаче источник Excel будет добавлен в поток данных, что позволит считывать данные поставщиков из исходного файла Excel. Источник Excel извлекает данные из листов или диапазонов в книгах Microsoft Excel. Дополнительные сведения см. в разделе [Источник Excel](http://msdn.microsoft.com/library/ms141683.aspx) .  
  
1.  Перетащите **Источник Excel** из области **Другие источники** на **панели элементов служб SSIS** на вкладке **Поток данных** .  
  
2.  Щелкните правой кнопкой мыши **источник Excel** на вкладке **Поток данных** и нажмите кнопку **Переименовать**.  
  
3.  Введите **Считывание данных о поставщиках из файла Excel** и нажмите клавишу **ВВОД**.  
  
4.  Дважды щелкните файл **Считывание данных о поставщиках из файла Excel** , чтобы открыть диалоговое окно **Редактор источника «Excel»** .  
  
5.  В диалоговом окне **Редактор источника «Excel»** нажмите **Создать** , чтобы создать соединение Excel.  
  
6.  В диалоговом окне **Диспетчер соединений Excel** выберите **Обзор**и выберите файл **Suppliers.xls** в папке **Учебник EIM** . Убедитесь, что выбрано значение **Microsoft Excel 97-2003** в поле **Версия Excel** и нажмите кнопку **ОК**.  
  
     ![Диалоговое окно «Диспетчер соединений с Excel»](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-01.jpg "диалоговое окно диспетчера соединений с Excel")  
  
7.  В диалоговом окне **Редактор источника «Excel»** выберите **IncomingSuppliers$** в раскрывающемся списке **Имя листа Excel** .  
  
     ![Имя листа Excel — Incoming Suppliers$](../../2014/tutorials/media/et-addingexcelsourcetothedataflow-02.jpg "имя листа Excel — Incoming Suppliers$")  
  
8.  Нажмите кнопку **Просмотр** , чтобы просмотреть данные в файле Excel.  
  
9. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
10. Перетащите преобразование **Очистка DQS** из области **Другие преобразования** на **панели элементов служб SSIS** на вкладку **Поток данных** в источнике **Считывание данных о поставщиках из файла Excel**. Преобразование «Очистка DQS» использует службы Data Quality Services (DQS) для исправления данных путем применения утвержденных правил в базе знаний. Это преобразование во время выполнения создает проект очистки DQS на сервере служб DQS. Дополнительные сведения см. в разделе [Преобразование «Очистка DQS»](http://msdn.microsoft.com/library/ee677619.aspx) .  
  
## <a name="next-step"></a>Следующий шаг  
 [Задача 7. Добавление преобразования "Очистка DQS" в поток данных](../integration-services/data-flow/data-flow.md)  
  
  