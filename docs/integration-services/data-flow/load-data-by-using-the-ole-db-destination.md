---
title: "Загрузка данных с помощью назначения «OLE DB» | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: eada84a10a9163c3a5bf0757def7948e18bf35da
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="load-data-by-using-the-ole-db-destination"></a>Загрузка данных с помощью назначения «OLE DB»
  Чтобы добавить и настроить назначение «OLE DB», в пакет уже должны быть включены хотя бы одна задача потока данных и один источник данных.  
  
### <a name="to-load-data-using-an-ole-db-destination"></a>Загрузка данных с помощью целевого объекта OLE DB  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Выберите вкладку **Поток данных** и перетащите из **области элементов**целевой объект OLE DB в область конструктора.  
  
4.  Подключите назначение «OLE DB» к потоку данных, перетащив соединитель из источника данных или предыдущего преобразования на назначение.  
  
5.  Дважды щелкните целевой объект OLE DB.  
  
6.  В диалоговом окне **Редактор назначения «OLE DB»** на странице **Диспетчер соединений** выберите уже существующий диспетчер соединений OLE DB или щелкните **Создать** , чтобы создать новый. Дополнительные сведения см. в статье [OLE DB Connection Manager](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
7.  Выберите метод доступа к данным.  
  
    -   **Таблица или представление** .    Выберите в базе данных таблицу или представление, содержащие данные.  
  
    -   **Быстрая загрузка таблицы или представления** . Выберите в базе данных таблицу или представление, содержащие данные, а затем определите параметры быстрой загрузки: **Сохранять ИД**, **Сохранять значения NULL**, **Блокировка таблицы**, **Проверочные ограничения**, **Строк на пакет**или **Макс. фиксируемый размер вставок**.  
  
    -   **Переменная имени представления или имени таблицы** . Выберите пользовательскую переменную, содержащую имя таблицы или представления в базе данных.  
  
    -   **Быстрая загрузка переменной имени представления или имени таблицы** . Выберите пользовательскую переменную, содержащую имя таблицы или представления в базе данных, а затем определите параметры быстрой загрузки.  
  
    -   **Команда SQL** .    Введите команду SQL или щелкните **Создать запрос** , чтобы создать команду SQL с помощью **Построителя запросов**.  
  
8.  Щелкните **Сопоставления** и сопоставьте столбцы из списка **Доступные входные столбцы** со столбцами из списка **Доступные целевые столбцы** , перетаскивая столбцы из одного списка в другой.  
  
    > [!NOTE]  
    >  Целевой объект OLE DB автоматически свяжет столбцы с одинаковыми именами.  
  
9. Чтобы настроить выход ошибок, щелкните **Вывод ошибок**. Дополнительные сведения см. в статье [Debugging Data Flow](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
10. Нажмите кнопку **ОК**.  
  
11. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также  
 [Назначение «OLE DB»](../../integration-services/data-flow/ole-db-destination.md)   
 [Преобразования служб Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Пути служб Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Задача потока данных](../../integration-services/control-flow/data-flow-task.md)  
  
  
