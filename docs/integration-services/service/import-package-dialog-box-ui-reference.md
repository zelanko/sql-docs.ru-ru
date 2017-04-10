---
title: "Диалоговое окно &#171;Импорт пакета&#187; справочника по пользовательскому интерфейсу | Microsoft Docs"
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
  - "sql13.dts.dtsserver.importpackage.f1"
helpviewer_keywords: 
  - "диалоговое окно «Импорт пакета»"
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# Диалоговое окно &#171;Импорт пакета&#187; справочника по пользовательскому интерфейсу
  Диалоговое окно **Импорт пакета** , доступное в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], позволяет импортировать пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и задавать или изменять уровень защиты пакета.  
  
## Параметры  
 **Размещение пакета**  
 Выберите тип места хранения, в которое импортировать пакет. Доступны следующие параметры:  
  
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
 Введите путь к пакету или нажмите кнопку просмотра **(…)** и определите местоположение пакета.  
  
 **Имя пакета**  
 При необходимости переименуйте пакет. По умолчанию это имя импортируемого пакета.  
  
 **Уровень защиты**  
 Щелкните кнопку просмотра **(…)** и измените уровень защиты в диалоговом окне **Уровень защиты пакета**. Дополнительные сведения см. в разделе [Диалоговое окно уровня защиты пакета и проекта](../../integration-services/packages/package-and-project-protection-level-dialog-box.md).  
  
## См. также  
 [Сохранение копии пакета](../Topic/Save%20Copy%20of%20Package.md)   
 [Диалоговое окно «Экспорт пакета» справочника по пользовательскому интерфейсу](../../integration-services/service/export-package-dialog-box-ui-reference.md)   
 [Сохранение пакетов](../../integration-services/save-packages.md)   
 [Импорт и экспорт пакетов (службы SSIS)](../../integration-services/service/import-and-export-packages-ssis-service.md)  
  
  