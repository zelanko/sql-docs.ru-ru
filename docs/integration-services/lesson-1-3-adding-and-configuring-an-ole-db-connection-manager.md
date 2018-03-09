---
title: "Шаг 3. Добавление и настройка диспетчера соединений OLE DB | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: tutorial
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 86d3e42b79efd2f2541c575b2c860b0a5cb4f41b
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="lesson-1-3---adding-and-configuring-an-ole-db-connection-manager"></a>Занятие 1–3. Добавление и настройка диспетчера соединений OLE DB
После добавления диспетчера соединений с неструктурированными файлами для подключения к источникам данных предстоит добавить диспетчер соединений OLE DB для соединения с назначением. Диспетчер соединений OLE DB позволяет пакету получать данные из любого источника данных, совместимого с OLE DB, а также загружать данные в такой источник данных. Используя диспетчер соединений OLE DB, можно указать для соединения сервер, метод проверки подлинности и базу данных по умолчанию.  
  
На этом занятии будет создан диспетчер соединений OLE DB, использующий проверку подлинности Windows для подключения к локальному экземпляру **AdventureWorksDB2012**. На создаваемый диспетчер соединений OLE DB также будут ссылаться другие компоненты, которые будут созданы позже в ходе работы с этим учебником, такие, как преобразование «Уточняющий запрос» и назначение OLE DB.  
  
### <a name="add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a>Добавление и настройка диспетчера соединений OLE DB для пакета служб SSIS  
  
1.  Щелкните правой кнопкой мыши область **Диспетчеры соединений** и выберите команду **Создать соединение OLE DB**.  
  
2.  В диалоговом окне **Настройка диспетчера соединений OLE DB** нажмите кнопку **Создать**.  
  
3.  Введите **localhost**в поле **Имя сервера**.  
  
    Если в качестве имени сервера указано значение localhost, диспетчер соединений соединяется с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , расположенном по умолчанию на локальном компьютере. Чтобы использовать удаленный экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], замените localhost именем сервера, с которым нужно соединиться.  
  
4.  Убедитесь, что в группе **Вход на сервер** выбран вариант **Использовать проверку подлинности Windows** .  
  
5.  В группе **Соединение с базой данных** в окне **Выберите или введите имя базы данных** введите или выберите имя **AdventureWorksDW2012**.  
  
6.  Нажмите кнопку **Проверить соединение** , чтобы убедиться, что параметры соединения указаны правильно.  
  
7.  Нажмите кнопку **ОК**.  
  
8.  Нажмите кнопку **ОК**.  
  
9. Убедитесь, что на панели **Подключение к данным** в диалоговом окне **Настройка диспетчера соединений OLE DB** выбрано значение **localhost.AdventureWorksDW2012** .  
  
10. Нажмите кнопку **ОК**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Этап 4. Добавление задачи потока данных в пакет](../integration-services/lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a>См. также:  
[Диспетчер соединений OLE DB](../integration-services/connection-manager/ole-db-connection-manager.md)  
  
