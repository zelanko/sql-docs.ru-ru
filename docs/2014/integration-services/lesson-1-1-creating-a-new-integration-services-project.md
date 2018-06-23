---
title: Шаг 1. Создание нового проекта служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f14521b5-941e-443b-8f5e-385f98e37fbf
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 3237d8a39b1d53b60fca2fcd65da0619d74a6300
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187784"
---
# <a name="step-1-creating-a-new-integration-services-project"></a>Шаг 1. Создание нового проекта служб Integration Services
  Первым шагом создания пакета в службах [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] будет создание проекта служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Этот проект содержит шаблоны для объектов (источников данных, представлений источников данных и пакетов), которые используются в решении преобразования данных.  
  
 Пакеты, которые будут создаваться в этом учебнике по службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , преобразуют значения, зависящие от локаля и региональных стандартов. Если компьютер не настроен на использование регионального параметра «Английский (США)», необходимо установить дополнительные свойства в пакете. Пакеты, использовавшиеся на занятиях 2–5, скопированы из пакета, созданного на занятии 1, поэтому в скопированных пакетах не обязательно обновлять свойства, зависящие от языка и региональных стандартов.  
  
> [!NOTE]  
>  Для выполнения упражнений этого учебника требуется Microsoft SQL Server Data Tools.  
>   
>  Дополнительные сведения об установке SQL Server Data Tools см. в разделе [Загрузка SQL Server Data Tools](http://msdn.microsoft.com/data/hh297027).  
  
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
 [Шаг 2. Добавление и настройка диспетчера подключения неструктурированных файлов](lesson-1-2-adding-and-configuring-a-flat-file-connection-manager.md)  
  
  