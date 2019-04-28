---
title: Предоставление разрешений администратора сервера (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- administrator rights [Analysis Services]
- server-wide administrative permissions [Analysis Services]
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8df7e950f300028b2246450bf29ed0e8776f2cd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62703681"
---
# <a name="grant-server-administrator-permissions-analysis-services"></a>Предоставление разрешений администратора сервера (службы Analysis Services)
  Члены роли администратора сервера в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеют неограниченный доступ ко всем объектам и данным данного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Для выполнения любых задач на уровне сервера, например для создания или обработки базы данных, изменения свойств сервера или запуска трассировки (кроме обработки событий), пользователь должен быть членом роли администратора сервера.  
  
 Членство в ролях определяется при установке служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Пользователь, выполняющий программу установки, может добавить себя к этой роли или добавить другого пользователя при провизионировании сервера. Используя следующую процедуру, можно изменять членство в роли после установки.  
  
## <a name="modify-server-role-membership"></a>Изменение членства в роли сервера  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], в обозревателе объектов щелкните правой кнопкой мыши имя экземпляра и выберите пункт **Свойства**.  
  
2.  На панели **Выбор страницы** щелкните **Безопасность** и нажмите кнопку **Добавить** , расположенную в нижней части страницы, чтобы добавить к роли сервера одного или нескольких пользователей или групп Windows.  
  
     ![Добавить пользователей диалоговое окно в среде management studio](../media/ssas-serveradminadd.png "добавить пользователей диалоговое окно в среде management studio")  
  
 Во время установки программа установки SQL Server требует указания по крайней мере одной учетной записи пользователя в качестве администратора служб Analysis Services.  
  
 По умолчанию члены локальной группы администраторов автоматически получают права администраторов в службе Analysis Server. Хотя локальной группе явно не предоставлено членство в роли администратора сервера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , локальные администраторы могут создавать базы данных, создавать пользователей и разрешения и выполнять другие разрешенные системным администраторам задачи. Это настраивается. Он определяется `BuiltinAdminsAreServerAdmins` свойства сервера, которому присвоено значение **true** по умолчанию. Это свойство вы можете изменить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Security Properties](../server-properties/security-properties.md).  
  
 Ролями сервера вы можете также управлять с помощью объектов AMO. Дополнительные сведения см. в разделе [Разработка объектов управления аналитикой (объекты AMO)](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).  
  
## <a name="see-also"></a>См. также  
 [Предоставление доступа к объектам и операциям (службы Analysis Services)](../multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Роли безопасности (службы Analysis Services — многомерные данные)](../multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
