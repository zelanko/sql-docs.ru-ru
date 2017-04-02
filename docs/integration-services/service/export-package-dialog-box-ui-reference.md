---
title: "Диалоговое окно &#171;Экспорт пакета&#187; справочника по пользовательскому интерфейсу | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.dtsserver.exportpackage.f1"
helpviewer_keywords: 
  - "диалоговое окно «Экспорт пакета»"
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# Диалоговое окно &#171;Экспорт пакета&#187; справочника по пользовательскому интерфейсу
  Диалоговое окно **Экспорт пакета** , доступное в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], используется для экспорта пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] в другое место и, при необходимости, изменения уровня защиты пакета.  
  
## Параметры  
 **Размещение пакета**  
 Выберите тип хранилища для экспорта пакета. Доступны следующие параметры:  
  
 **SQL Server**  
  
 **Файловая система**  
  
 **Хранилище пакетов служб SSIS**  
  
 **Server**  
 Введите имя сервера или выберите его из списка.  
  
 **Проверка подлинности**  
 Выберите проверку подлинности Windows или проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Этот параметр доступен, только если в качестве места хранения указан [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  При возможности используйте проверку подлинности Windows.  
  
 **Тип проверки подлинности**  
 Выберите тип проверки подлинности.  
  
 **Имя пользователя**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите пароль.  
  
 **Путь пакета**  
 Введите путь модуля или нажмите кнопку обзора **(...)** и выберите папку, в которой должен быть сохранен пакет.  
  
 **Уровень защиты**  
 Нажмите кнопку обзора **(...)** и обновите уровень защиты в диалоговом окне **Уровень защиты пакета**. Дополнительные сведения см. в разделе [Диалоговое окно уровня защиты пакета и проекта](../../integration-services/packages/package-and-project-protection-level-dialog-box.md).  
  
## См. также  
 [Сохранение копии пакета](../Topic/Save%20Copy%20of%20Package.md)   
 [Диалоговое окно «Импорт пакета» справочника по пользовательскому интерфейсу](../../integration-services/service/import-package-dialog-box-ui-reference.md)   
 [Сохранение пакетов](../../integration-services/save-packages.md)   
 [Импорт и экспорт пакетов (службы SSIS)](../../integration-services/service/import-and-export-packages-ssis-service.md)  
  
  