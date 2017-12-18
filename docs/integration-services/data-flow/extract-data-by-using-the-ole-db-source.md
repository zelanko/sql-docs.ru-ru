---
title: "Извлечение данных с помощью источника \"OLE DB\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
caps.latest.revision: "23"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 67082fa6742c230b5a60e98a553c975b9fab228d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="extract-data-by-using-the-ole-db-source"></a>Извлечение данных с помощью источника OLE DB
  Чтобы добавить и настроить источник OLE DB, пакет уже должен иметь по крайней мере одну задачу потока данных.  
  
### <a name="to-extract-data-using-an-ole-db-source"></a>Извлечение данных при помощи источника OLE DB  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Щелкните вкладку **Поток данных** и перетащите источник OLE DB из **области элементов**в область конструктора.  
  
4.  Дважды щелкните источник OLE DB.  
  
5.  В диалоговом окне **Редактор источника OLE DB** на странице **Диспетчер соединений** выберите существующий диспетчер соединений OLE DB или нажмите **Создать** , чтобы создать новый диспетчер соединений. Дополнительные сведения см. в статье [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
6.  Выберите метод доступа к данным.  
  
    -   **Таблица или представление** .   Выберите таблицу или представление в базе данных, с которой соединяется диспетчер соединений OLE DB.  
  
    -   **Переменная имени представления или имени таблицы** . Выберите пользовательскую переменную, которая содержит имя таблицы или представления в базе данных, с которой соединяется диспетчер соединений OLE DB.  
  
    -   **Команда SQL** .   Введите команду SQL или нажмите **Создать запрос** , чтобы написать команду SQL при помощи **Построителя запросов**.  
  
        > [!NOTE]  
        >  Команда может включать параметры. Дополнительные сведения см. в разделе [Сопоставления параметров запросов с переменными в компонентах потока данных](../../integration-services/data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md).  
  
    -   **Команда SQL из переменной** . Выберите пользовательскую переменную, содержащую команду SQL.  
  
        > [!NOTE]  
        >  Переменные должны определяться в области той же задачи потока данных, которая содержит источник OLE DB, либо в области того же пакета. Кроме того, переменная должна иметь строковый тип данных.  
  
7.  Чтобы обновить сопоставление между внешними и выходными столбцами, щелкните **Столбцы** и выберите другие столбцы в списке **Внешний столбец** .  
  
8.  Существует дополнительная возможность обновления имен выходных столбцов путем редактирования значений в списке **Выходной столбец** .  
  
9. Чтобы настроить выход ошибок, щелкните **Вывод ошибок**. Дополнительные сведения см. в статье [Debugging Data Flow](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
10. Можно нажать **Предварительный просмотр** , чтобы просмотреть до 200 строк данных, извлеченных из источника OLE DB.  
  
11. Нажмите кнопку **ОК**.  
  
12. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Источник OLE DB](../../integration-services/data-flow/ole-db-source.md)   
 [Преобразования служб Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Пути служб Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Задача потока данных](../../integration-services/control-flow/data-flow-task.md)  
  
  
