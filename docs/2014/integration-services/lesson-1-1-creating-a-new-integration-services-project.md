---
title: Шаг 1. Создание нового проекта служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2513a698fc073c751613e8e387d41ddb3e0fe9e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62891767"
---
# <a name="step-1-creating-a-new-integration-services-project"></a>Шаг 1. Создание нового проекта служб Integration Services
  Первым шагом создания пакета в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] будет создание проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Этот проект содержит шаблоны для объектов (источников данных, представлений источников данных и пакетов), которые используются в решении преобразования данных.  
  
 Пакеты, которые будут создаваться в этом учебнике по службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , преобразуют значения, зависящие от локаля и региональных стандартов. Если компьютер не настроен на использование регионального параметра «Английский (США)», необходимо установить дополнительные свойства в пакете. Пакеты, использовавшиеся на занятиях 2–5, скопированы из пакета, созданного на занятии 1, поэтому в скопированных пакетах не обязательно обновлять свойства, зависящие от языка и региональных стандартов.  
  
> [!NOTE]  
>  Для выполнения упражнений этого учебника требуется Microsoft SQL Server Data Tools.  
>   
>  Дополнительные сведения об установке SQL Server Data Tools см. в разделе [Загрузка SQL Server Data Tools](https://msdn.microsoft.com/data/hh297027).  
  
### <a name="to-create-a-new-integration-services-project"></a>Создание нового проекта служб Integration Services  
  
1.  В меню **Пуск** последовательно укажите пункты **Все программы**, **Microsoft SQL Server**и выберите **SQL Server Data Tools**.  
  
2.  В меню **Файл** укажите **Создать**и выберите пункт **Проект** , чтобы создать новый проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
3.  В диалоговом окне **Создать проект** разверните узел **Бизнес-аналитика** в категории **Установленные шаблоны**и выберите **Проект служб Integration Services** на панели **Шаблоны** .  
  
4.  В поле **Имя** измените заданное по умолчанию имя на **Учебник по службам SQL Server Integration Services**. При необходимости снимите флажок **Создать каталог для решения** .  
  
5.  Согласитесь с местоположением по умолчанию или нажмите кнопку **Обзор** , чтобы найти нужную папку. В диалоговом окне **Расположение проекта** щелкните папку и нажмите кнопку **Выбрать папку**.  
  
6.  Нажмите кнопку **ОК**.  
  
     По умолчанию будет создан пустой пакет с именем **Package.dtsx**и добавлен к проекту в узле «Пакеты служб SSIS».  
  
7.  На панели инструментов **обозревателя решений** щелкните правой кнопкой мыши файл **Package.dtsx**, выберите команду **Переименовать**и переименуйте пакет по умолчанию в **Урок 1.dtsx**.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Шаг 2. Добавление и настройка диспетчера соединений с неструктурированными файлами](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  
