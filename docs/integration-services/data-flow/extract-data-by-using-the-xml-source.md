---
title: Извлечение данных с помощью XML-источника | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], XML
- XML source [Integration Services]
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f149ca01b71b7611264f28d14532d7827554585f
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71292545"
---
# <a name="extract-data-by-using-the-xml-source"></a>Извлечение данных с помощью XML-источника

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Чтобы добавить и настроить источник XML, пакет должен уже содержать не менее одной задачи потока данных.  
  
### <a name="to-extract-data-using-an-xml-source"></a>Извлечение данных с использованием XML-источника  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток данных** , затем из **области элементов**перетащите источник XML в область конструктора.  
  
4.  Дважды щелкните источник XML.  
  
5.  В **Редакторе XML-источника**на странице **Диспетчер соединений** выберите режим доступа к данным.  
  
    -   Для режима получения доступа **Расположение XML-файла** нажмите кнопку **Обзор** и найдите папку, содержащую XML-файл.  
  
    -   Для режима получения доступа **XML-файл из переменной** выберите пользовательскую переменную, содержащую путь XML-файла.  
  
    -   Для режима получения доступа **XML-данные из переменной** выберите пользовательскую переменную, содержащую XML-данные.  
  
    > [!NOTE]  
    >  Переменные должны быть определены в области задачи потока данных, которая содержит источник XML, или в области пакета. Кроме того, переменная должна иметь строковый тип данных.  
  
6.  Чтобы указать, что XML-документ включает сведения о схеме, по своему усмотрению выберите **Использовать встроенную схему** .  
  
7.  Чтобы указать внешний язык определения XML-схемы (XSD) для XML-файла, выполните одно из следующих действий.  
  
    -   Нажмите кнопку **Обзор** для нахождения существующего XSD-файла.  
  
    -   Нажмите кнопку **Сформировать XSD** , чтобы сформировать XSD из XML-файла.  
  
8.  Чтобы обновить имена входных столбцов, щелкните **Столбцы** и отредактируйте значения в списке **Выходной столбец** .  
  
9. Чтобы настроить выход ошибок, щелкните **Вывод ошибок**. Дополнительные сведения см. в статье [Отладка потока данных](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
10. Нажмите кнопку **ОК**.  
  
11. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [XML-источник](../../integration-services/data-flow/xml-source.md)   
 [Преобразования служб Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Пути служб Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Задача потока данных](../../integration-services/control-flow/data-flow-task.md)  
  
  
