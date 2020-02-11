---
title: Сохранить копию пакета | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 649c972b001a0627a568f0bd9e1ac2b42d5175ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66056320"
---
# <a name="save-copy-of-package"></a>Сохранение копии пакета
  Используйте диалоговое окно **Сохранение копии пакета** , доступное в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], чтобы сохранить копию пакета служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] из среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] в другое местоположение и в случае необходимости изменить уровень защиты пакета.  
  
## <a name="options"></a>Параметры  
 **Расположение пакета**  
 Выберите тип места хранения, в котором должна быть сохранена копия пакета. Доступны следующие варианты:  
  
 **SQL Server**  
  
 **Файловая система**  
  
 **Хранилище пакетов служб SSIS**  
  
 **Сервер**  
 Введите имя сервера или выберите его из списка. Этот параметр доступен, только если в качестве места хранения указан **SQL Server** или **Хранилище пакетов служб SSIS**.  
  
 **Аутентификация**  
 Выберите проверку подлинности Windows или проверку подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Этот параметр доступен, только если в качестве места хранения указан [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  При возможности используйте проверку подлинности Windows.  
  
 **Authentication type (Тип проверки подлинности)**  
 Выберите тип проверки подлинности.  
  
 **User name**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите пароль.  
  
 **Путь к пакету**  
 Введите путь к пакету или нажмите кнопку обзора **(...)** и найдите папку, в которой будет сохранен пакет.  
  
 **Уровень защиты**  
 Нажмите кнопку обзора **(...)** и обновите уровень защиты в диалоговом окне **уровень защиты пакета** . Дополнительные сведения см. в разделе [Диалоговое окно уровня защиты пакета и проекта](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по пользовательскому интерфейсу диалогового окна "Импорт пакета"](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [Справочник по пользовательскому интерфейсу диалогового окна экспорта пакета](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Сохранение пакетов](save-packages.md)   
 [Импорт и экспорт пакетов &#40;служб SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
