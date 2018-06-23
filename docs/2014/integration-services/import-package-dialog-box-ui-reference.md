---
title: Импорт пакета диалоговое окно пользовательского интерфейса в справочник | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.dtsserver.importpackage.f1
helpviewer_keywords:
- Import Package dialog box
ms.assetid: 0e5fb127-c7ff-4dfa-b90e-d9bcf0ce763b
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: bc1c4ab12c5617d8c60e898587b664f552709299
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193600"
---
# <a name="import-package-dialog-box-ui-reference"></a>Диалоговое окно «Импорт пакета» справочника по пользовательскому интерфейсу
  Диалоговое окно **Импорт пакета** , доступное в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], позволяет импортировать пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и задавать или изменять уровень защиты пакета.  
  
## <a name="options"></a>Параметры  
 **Размещение пакета**  
 Выберите тип места хранения, в которое импортировать пакет. Доступны следующие параметры:  
  
 **SQL Server**  
  
 **Файловая система**  
  
 **Хранилище пакетов служб SSIS**  
  
 **Server**  
 Введите имя сервера или выберите его из списка.  
  
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
 Введите путь к пакету или нажмите кнопку просмотра **(…)** и определите местоположение пакета.  
  
 **Имя пакета**  
 При необходимости переименуйте пакет. По умолчанию это имя импортируемого пакета.  
  
 **Уровень защиты**  
 Щелкните кнопку просмотра **(…)** и измените уровень защиты в диалоговом окне **Уровень защиты пакета** . Дополнительные сведения см. в разделе [Диалоговое окно уровня защиты пакета и проекта](../../2014/integration-services/package-and-project-protection-level-dialog-box.md).  
  
## <a name="see-also"></a>См. также  
 [Сохранение копии пакета](../../2014/integration-services/save-copy-of-package.md)   
 [Экспорт пакета диалоговое окно пользовательского интерфейса в справочник](../../2014/integration-services/export-package-dialog-box-ui-reference.md)   
 [Сохранение пакетов](save-packages.md)   
 [Импорт и экспорт пакетов &#40;службы SSIS&#41;](../../2014/integration-services/import-and-export-packages-ssis-service.md)  
  
  