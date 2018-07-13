---
title: Редактор назначения SQL (страница «Диспетчер соединений») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.connection.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 423e1654-54af-47c6-ab6f-98670534557d
caps.latest.revision: 36
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bb74d6cb0a3496718ef6768ffc69456b76aaf784
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195694"
---
# <a name="sql-destination-editor-connection-manager-page"></a>Редактор назначения «SQL» (страница «Диспетчер соединений»)
  Страница **Диспетчер соединений** диалогового окна **Редактор назначения «SQL»** используется для задания сведений об источнике данных и для предварительного просмотра результатов. Назначение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] загружает данные в таблицы или представления в базе данных [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Дополнительные сведения о назначении «SQL Server» см. в разделе [SQL Server Destination](data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Параметры  
 **Диспетчер соединений OLE DB**  
 Выберите существующий диспетчер подключений из списка или создайте новое соединение, выбрав пункт **Создать**.  
  
 **Создать**  
 Создайте новое соединение с помощью диалогового окна **Настройка диспетчера соединений OLE DB** .  
  
 **Использовать таблицу или представление**  
 Выберите существующую таблицу или представление из списка или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новую таблицу с помощью диалогового окна **Создание таблицы** .  
  
> [!NOTE]  
>  При нажатии кнопки **Создать**службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] по умолчанию формируют инструкцию CREATE TABLE на основе подключенного источника данных. Эта инструкция CREATE TABLE не включает атрибут FILESTREAM, даже если исходная таблица содержит столбец, для которого объявлен атрибут FILESTREAM. Чтобы запустить компонент служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] с атрибутом FILESTREAM, сначала следует создать хранилище FILESTREAM в целевой базе данных. Затем добавьте атрибут FILESTREAM к инструкции CREATE TABLE в диалоговом окне **Создание таблицы** . Дополнительные сведения см. в разделе [Данные большого двоичного объекта (SQL Server)](../relational-databases/blob/binary-large-object-blob-data-sql-server.md).  
  
 **Предварительный просмотр**  
 Просмотрите предварительные результаты, используя диалоговое окно **Предварительный просмотр результатов запроса** . В окне «Предварительный просмотр» может отображаться до 200 строк.  
  
## <a name="see-also"></a>См. также  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения SQL &#40;страница «сопоставления»&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [Редактор назначения SQL &#40;страница "Дополнительно"&#41;](../../2014/integration-services/sql-destination-editor-advanced-page.md)   
 [Выполнение массовой загрузки данных с помощью назначения «SQL Server»](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
