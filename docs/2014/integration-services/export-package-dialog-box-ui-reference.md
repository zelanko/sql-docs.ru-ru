---
title: Справочник по пользовательскому интерфейсу диалогового окна экспорта пакета | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.exportpackage.f1
helpviewer_keywords:
- Export Package dialog box
ms.assetid: 3742fe8a-ef57-444d-b2fb-cb25d16bae97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6085a6fde388cf65ed9fa8eddaf8ffc898a29999
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437401"
---
# <a name="export-package-dialog-box-ui-reference"></a>Диалоговое окно «Экспорт пакета» справочника по пользовательскому интерфейсу
  Диалоговое окно **Экспорт пакета** , доступное в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], используется для экспорта пакета служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в другое место и, при необходимости, изменения уровня защиты пакета.  
  
## <a name="options"></a>Параметры  
 **Размещение пакета**  
 Выберите тип хранилища для экспорта пакета. Доступны следующие параметры.  
  
 **SQL Server**  
  
 **Файловая система**  
  
 **Хранилище пакетов служб SSIS**  
  
 **Server**  
 Введите имя сервера или выберите его из списка.  
  
 **Authentication**  
 Выберите проверку подлинности Windows или проверку подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Этот параметр доступен, только если в качестве места хранения указан [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  При возможности используйте проверку подлинности Windows.  
  
 **Тип проверки подлинности**  
 Выберите тип проверки подлинности.  
  
 **User name**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите пароль.  
  
 **Путь пакета**  
 Введите путь к пакету или нажмите кнопку обзора **(...)** и найдите папку, в которой будет сохранен пакет.  
  
 **Уровень защиты**  
 Нажмите кнопку обзора **(...)** и обновите уровень защиты в диалоговом окне **уровень защиты пакета** . Дополнительные сведения см. в разделе [Диалоговое окно уровня защиты пакета и проекта](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>См. также  
 [Сохранить копию пакета](../../2014/integration-services/save-copy-of-package.md)   
 [Справочник по пользовательскому интерфейсу диалогового окна "Импорт пакета"](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [Сохранение пакетов](save-packages.md)   
 [Импорт и экспорт пакетов (службы SSIS)](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
