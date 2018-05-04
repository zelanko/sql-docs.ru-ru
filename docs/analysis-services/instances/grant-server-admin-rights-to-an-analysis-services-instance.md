---
title: Предоставление прав администратора сервера для экземпляра служб Analysis Services | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 080e12b4c6c4939ff97cef4a521ef6c073b3c632
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="grant-server-admin-rights-to-an--analysis-services-instance"></a>Предоставление прав администратора сервера для экземпляра служб Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Члены роли администратора сервера в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеют неограниченный доступ ко всем объектам и данным данного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Для выполнения любых задач на уровне сервера, например для создания или обработки базы данных, изменения свойств сервера или запуска трассировки (кроме обработки событий), пользователь должен быть членом роли администратора сервера.  
  
 Членство в ролях определяется при установке служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Пользователь, выполняющий программу установки, может добавить себя или другого пользователя к этой роли. Чтобы продолжить установку, необходимо указать хотя бы одного администратора.  
  
 По умолчанию члены локальной группы администраторов автоматически получают права администраторов в службе Analysis Server. Хотя локальной группе явно не предоставлено членство в роли администратора сервера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , локальные администраторы могут создавать базы данных, создавать пользователей и разрешения и выполнять другие разрешенные системным администраторам задачи. Кроме этого, можно настроить неявное предоставление прав администратора. Эта возможность определяется свойством сервера **BuiltinAdminsAreServerAdmins** , имеющим по умолчанию значение **true** . Это свойство вы можете изменить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Security Properties](../../analysis-services/server-properties/security-properties.md).  
  
 После установки можно изменить членство в роли, чтобы добавить дополнительных пользователей с полными правами доступа к службе. Ролями сервера вы можете также управлять с помощью объектов AMO. Дополнительные сведения см. в разделе [Разработка объектов управления аналитикой (объекты AMO)](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предусматривают несколько очень детализированных ролей обработка и запросы на уровне сервера, базы данных и объекта. Инструкции по использованию этих ролей см. в разделе [Роли и разрешения (службы Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md).  
  
## <a name="modify-server-role-membership"></a>Изменение членства в роли сервера  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], в обозревателе объектов щелкните правой кнопкой мыши имя экземпляра и выберите пункт **Свойства**.  
  
2.  На панели **Выбор страницы** щелкните **Безопасность** и нажмите кнопку **Добавить** , расположенную в нижней части страницы, чтобы добавить к роли сервера одного или нескольких пользователей или групп Windows.  
  
     ![Добавить пользователей диалоговое окно в среде management studio](../../analysis-services/instances/media/ssas-serveradminadd.png "добавить пользователей диалоговое окно в среде management studio")  
  
### <a name="add-computer-accounts"></a>Добавление учетных записей компьютеров  
 С помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно сделать учетную запись компьютера участником группы администраторов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
1.  В диалоговом окне **Выбор пользователей или групп** щелкните **Расположение**.  
  
2.  Выберите домен, к которому принадлежат компьютеры, какие необходимо добавить, или выберите **Весь каталог** и нажмите кнопку **ОК**.  
  
3.  Щелкните **Типы объектов**.  
  
4.  Установите флажок **Компьютеры** и нажмите кнопку **ОК**.  
  
     ![Добавление учетных записей компьютеров в качестве администраторов служб ssas](../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "добавить учетные записи компьютеров в качестве администраторов служб ssas")  
  
5.  В текстовом поле **Введите имена объектов для выбора** введите имя компьютера и нажмите кнопку **Проверить имена** , чтобы проверить, находится ли учетная запись компьютера в текущем расположении. Если учетная запись компьютера не найдена, проверьте имя компьютера и домена, членом которого является компьютер.  
  
## <a name="nt-servicessastelemetry-account"></a>Учетная запись NT Service\SSASTelemetry  
 **NT Service/SSASTelemetry** — это учетная запись компьютера с ограниченными правами, которая создается во время установки и используется исключительно для реализации службы программы улучшения качества программного обеспечения службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Для выполнения нескольких команд обнаружения этой службе необходимы права администратора на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в разделах [Customer Experience Improvement Program for SQL Server Data Tools](../../sql-server/customer-experience-improvement-program-for-sql-server-data-tools.md) и [Microsoft SQL Server Privacy Statement](http://msdn.microsoft.com/library/57769f4a-5689-49a1-8298-e3c0db5106f8) .  
  
## <a name="see-also"></a>См. также  
 [Предоставление доступа к объектам и операциям (службы Analysis Services)](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Роли безопасности & #40; Analysis Services — многомерные данные & #41;](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  
