---
title: "Настройка редакторов (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7c7a8ef-f561-4258-a7b6-c445dba69f87
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2df9024353df34fc5b7860bae2eaa5b633c06b9f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="configure-editors-sql-server-management-studio"></a>Настройка редакторов (среда SQL Server Management Studio)
  Параметры работы редакторов [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] настраиваются для каждого редактора отдельно.  
  
## <a name="settng-editor-options"></a>Настройка параметров редактора  
 Большинство параметров редакторов задаются в диалоговом окне **Параметры** . Чтобы открыть это окно, выберите в меню **Сервис** пункт **Параметры…** . В диалоговом окне **Параметры** откройте узел **Текстовый редактор** в левой панели, чтобы задать параметры редактирования кода и текста. Вложенные узлы в узле «Текстовый редактор» относятся к определенным редакторам:  
  
1.  **Все языки** — параметры, заданные с помощью этого узла, относятся ко всем редакторам [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] . Можно переопределить эти настройки с помощью других узлов, задав другие параметры для определенного редактора.  
  
2.  **Простой текст** — параметры, заданные с помощью этого узла, относятся к редакторам MDX, DMX и текстовым редакторам.  
  
3.  **Transact-SQL** — параметры, заданные с помощью этого узла, относятся к редактору запросов компонента Database Engine.  
  
4.  **XML** — параметры, заданные с помощью этого узла, относятся к редактору XML для аналитики.  
  
 Откройте узел **Выполнение запросов** или **Результаты запросов** , чтобы настроить выполнение запросов и способ отображения результатов.  
  
## <a name="editor-configuration-tasks"></a>Задачи конфигурации редакторов  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Описывается, каким образом можно настроить открытие редактора двойным щелчком файла с указанным расширением в проводнике Windows.|[Связывание расширения файла с редактором кода](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)|  
|Описывается настройка шрифтов для улучшения отображения кода и текста.|[Изменение цвета, размера и стиля шрифта](../../relational-databases/scripting/change-font-color-size-and-style.md)|  
|Описывается способ просмотра свойств.|[Использование окна «Свойства» в среде Management Studio](../../relational-databases/scripting/use-the-properties-window-in-management-studio.md)|  
|Расположение страниц справки F1 в диалоговых окнах параметров редактора.|[Справка F1 страниц параметров запросов](http://msdn.microsoft.com/library/fad98caa-8a29-4b88-8464-f60a5c4fc00e)|  
  
  
