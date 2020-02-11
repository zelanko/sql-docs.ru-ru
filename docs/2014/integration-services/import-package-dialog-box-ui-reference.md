---
title: Справочник по пользовательскому интерфейсу диалогового окна "Импорт пакета" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3e36fae15f6f4220565bcc3d14c0e125ca6818f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058083"
---
# <a name="import-package-dialog-box-ui-reference"></a>Диалоговое окно «Импорт пакета» справочника по пользовательскому интерфейсу
  Диалоговое окно **Импорт пакета** , доступное в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], позволяет импортировать пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и задавать или изменять уровень защиты пакета.  
  
## <a name="options"></a>Параметры  
 **Расположение пакета**  
 Выберите тип места хранения, в которое импортировать пакет. Доступны следующие варианты:  
  
 **SQL Server**  
  
 **Файловая система**  
  
 **Хранилище пакетов служб SSIS**  
  
 **Сервер**  
 Введите имя сервера или выберите его из списка.  
  
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
 Введите путь к пакету или нажмите кнопку просмотра **(…)** и определите местоположение пакета.  
  
 **Имя пакета**  
 При необходимости переименуйте пакет. По умолчанию это имя импортируемого пакета.  
  
 **Уровень защиты**  
 Щелкните кнопку просмотра **(…)** и измените уровень защиты в диалоговом окне **Уровень защиты пакета**. Дополнительные сведения см. в разделе [Диалоговое окно уровня защиты пакета и проекта](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>См. также:  
 [Сохранить копию пакета](../../2014/integration-services/save-copy-of-package.md)   
 [Справочник по пользовательскому интерфейсу диалогового окна экспорта пакета](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Сохранение пакетов](save-packages.md)   
 [Импорт и экспорт пакетов &#40;служб SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  
