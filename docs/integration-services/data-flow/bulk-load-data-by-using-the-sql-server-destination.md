---
title: Выполнение массовой загрузки данных с помощью назначения "SQL Server" | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server destination
- loading data
- destinations [Integration Services], SQL Server
- inserting data
- bulk load [Integration Services]
ms.assetid: 8f982f85-a82e-4e2d-9cd8-cd2f85402d8e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf8e8c7bafb72b90edfe108c5702ad330bc3e700
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71293470"
---
# <a name="bulk-load-data-by-using-the-sql-server-destination"></a>Выполнение массовой загрузки данных с помощью назначения «SQL Server»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Чтобы добавить и настроить назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , пакет уже должен содержать как минимум одну задачу потока данных и один источник данных.  
  
### <a name="to-load-data-using-a-sql-server-destination"></a>Загрузка данных с помощью назначения SQL Server  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Поток данных** , затем из окна **Область элементов**перетащите назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в область конструктора.  
  
4.  Подключите назначение к источнику или предыдущему преобразованию в потоке данных, перетащив соединитель на назначение.  
  
5.  Дважды щелкните назначение.  
  
6.  В окне **Редактор назначений SQL Server**на странице **Диспетчер соединений** выберите существующий диспетчер соединений OLE DB или нажмите кнопку **Создать** в целях создания нового диспетчера соединений. Дополнительные сведения см. в разделе [Диспетчер соединений OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
7.  Чтобы указать таблицу или представление, в которое следует загружать данные, выполните одно из следующих действий.  
  
    -   Выберите существующую таблицу или представление.  
  
    -   Нажмите кнопку **Создать**, затем в диалоговом окне **Создание таблицы** введите инструкцию SQL, которая создает таблицу или представление.  
  
        > [!NOTE]  
        >  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] формируют инструкцию по умолчанию CREATE TABLE на основании подключенных источников данных. Эта инструкция CREATE TABLE не включает атрибут FILESTREAM, даже если исходная таблица содержит столбец, для которого объявлен атрибут FILESTREAM. Чтобы запустить компонент служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с атрибутом FILESTREAM, сначала следует создать хранилище FILESTREAM в целевой базе данных. Затем добавьте атрибут FILESTREAM к инструкции CREATE TABLE в диалоговом окне **Создание таблицы** . Дополнительные сведения см. в разделе [Данные большого двоичного объекта (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
8.  Нажмите кнопку **Сопоставления** и сопоставьте столбцы из списка **Доступные входные столбцы** со столбцами из списка **Доступные целевые столбцы** , перетащив столбцы из одного списка в другой.  
  
    > [!NOTE]  
    >  Назначение автоматически сопоставит столбцы с одинаковыми именами.  
  
9. Нажмите кнопку **Дополнительно** и настройте параметры массовой загрузки: **Сохранять ИД**, **Сохранять значения NULL**, **Блокировка таблицы**, **Проверять ограничения** и **Запускать триггеры**.  
  
     При необходимости укажите первую и последнюю входные строки для вставки, максимальное число ошибок до остановки операции вставки, а также столбцы, по которым сортируются вставляемые строки.  
  
    > [!NOTE]  
    >  Порядок сортировки определяется последовательностью, в которой перечислены столбцы.  
  
10. Нажмите кнопку **ОК**.  
  
11. Чтобы сохранить обновленный пакет, выберите пункт **Сохранить выбранные элементы** в меню **Файл** .  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Destination](../../integration-services/data-flow/sql-server-destination.md)   
 [Преобразования служб Integration Services](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Пути служб Integration Services](../../integration-services/data-flow/integration-services-paths.md)   
 [Задача потока данных](../../integration-services/control-flow/data-flow-task.md)  
  
  
