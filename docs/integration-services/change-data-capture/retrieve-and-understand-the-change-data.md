---
description: Получение и интерпретация измененных данных
title: Получение и интерпретация измененных данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f8c9a326ab700be3ebef26db7160323314f4af43
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457674"
---
# <a name="retrieve-and-understand-the-change-data"></a>Получение и интерпретация измененных данных

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  В потоке данных пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , выполняющего добавочную загрузку измененных данных, первая задача — выполнение запроса, который получает информацию об изменениях. Этот запрос выполняется внутри исходного компонента задачи потока данных. Затем можно использовать нисходящие преобразования и назначения, чтобы применить данные об изменениях к назначению.  
  
> [!NOTE]  
>  Создание запроса, содержащего возвращающую табличное значение функцию, является третьим шагом в процессе создания пакета, который осуществляет добавочную загрузку измененных данных. Дополнительные сведения об этом запросе см. в разделе [Создание функции для получения информации об изменениях](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md). Описание общего процесса создания пакета, выполняющего добавочную загрузку информации об изменениях, см. в разделе [Система отслеживания измененных данных (SSIS)](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## <a name="adding-the-data-flow-task"></a>Добавление задачи потока данных  
 В потоке данных пакета получаются измененные данные, отдельные строки на основе типа произошедших изменений, а затем изменения применяются к назначению.  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a>Добавление задачи потока данных к пакету  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]на вкладке **Поток управления** добавьте задачу потока данных.  
  
2.  Соедините предыдущую задачу, подготовившую строку запроса, с задачей потока данных.  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a>Настройка исходного компонента для выполнения запроса об изменениях  
 С помощью подготовленной и сохраненной в переменной строки запроса исходный компонент вызывает возвращающую табличное значение функцию, которая получает измененные данные.  
  
> [!NOTE]  
>  Дополнительные сведения о подготовленной и сохраненной в переменной строке запроса см. в разделе [Подготовка к запросу информации об изменениях](../../integration-services/change-data-capture/prepare-to-query-for-the-change-data.md). Дополнительные сведения о возвращающей табличное значение функции, которая получает данные об изменениях, см. в разделе [Создание функции для получения информации об изменениях](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md).  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a>Настройка источника OLE DB для получения измененных данных.  
  
1.  На вкладке [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Поток данных **среды** добавьте источник OLE DB.  
  
2.  На странице **Диспетчер соединений**в области **Редактор источника OLE DB** установите следующие параметры.  
  
    1.  Настройте допустимое соединение с базой данных-источником.  
  
    2.  В списке **Режим доступа к данным**выберите **Команда SQL из переменной**.  
  
    3.  В поле **Имя переменной**выберите **User::SqlDataQuery**.  
  
3.  В области **Редактор источника OLE DB**на странице **Столбцы** убедитесь, чтобы все необходимые столбцы были сопоставлены с выходными столбцами.  
  
## <a name="next-step"></a>Следующий шаг  
 После настройки источника OLE DB для получения измененных данных начинается проектирование потока данных в пакете.  
  
 **Следующий раздел:** [Обработка операций вставки, обновления и удаления](../../integration-services/change-data-capture/process-inserts-updates-and-deletes.md)  
  
  
