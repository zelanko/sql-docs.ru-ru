---
title: Сохранение копии пакета | Документация Майкрософт
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
- sql12.dts.designer.savecopyas.f1
helpviewer_keywords:
- Save Copy of Package dialog box
ms.assetid: 7b44c0d7-d8fa-4491-8836-0899f621d3a8
caps.latest.revision: 17
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: acbeb63fb7e816d432609a56bf6ba72463a5ea48
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260980"
---
# <a name="save-copy-of-package"></a>Сохранение копии пакета
  Используйте диалоговое окно **Сохранение копии пакета** , доступное в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], чтобы сохранить копию пакета служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] из среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] в другое местоположение и в случае необходимости изменить уровень защиты пакета.  
  
## <a name="options"></a>Параметры  
 **Размещение пакета**  
 Выберите тип места хранения, в котором должна быть сохранена копия пакета. Доступны следующие параметры:  
  
 **SQL Server**  
  
 **Файловая система**  
  
 **Хранилище пакетов служб SSIS**  
  
 **Server**  
 Введите имя сервера или выберите его из списка. Этот параметр доступен, только если в качестве места хранения указан **SQL Server** или **Хранилище пакетов служб SSIS**.  
  
 **Проверка подлинности**  
 Выберите проверку подлинности Windows или проверку подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Этот параметр доступен, только если в качестве места хранения указан [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  При возможности используйте проверку подлинности Windows.  
  
 **Тип проверки подлинности**  
 Выберите тип проверки подлинности.  
  
 **Имя пользователя**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите имя пользователя.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] укажите пароль.  
  
 **Путь пакета**  
 Введите путь модуля или нажмите кнопку обзора **(...)** и выберите папку, в которой должен быть сохранен пакет.  
  
 **Уровень защиты**  
 Нажмите кнопку обзора **(...)** и обновите уровень защиты в диалоговом окне **Уровень защиты пакета** . Дополнительные сведения см. в разделе [Диалоговое окно уровня защиты пакета и проекта](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>См. также  
 [Импорт пакета диалогового окна пользовательского интерфейса в справочник](../../2014/integration-services/import-package-dialog-box-ui-reference.md)   
 [Экспорт пакета диалоговое окно пользовательского интерфейса в справочник](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Сохранение пакетов](save-packages.md)   
 [Импорт и экспорт пакетов &#40;службы SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
