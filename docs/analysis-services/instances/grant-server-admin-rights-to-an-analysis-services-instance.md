---
title: "Предоставление прав администратора сервера для экземпляра служб Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "права администратора [службы Analysis Services]"
  - "административные разрешения уровня сервера [службы Analysis Services]"
ms.assetid: 20d1234b-a457-4a84-ae08-fe356870c466
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 37
---
# Предоставление прав администратора сервера для экземпляра служб Analysis Services
  Члены роли администратора сервера в экземпляре служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеют неограниченный доступ ко всем объектам и данным данного экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Для выполнения любых задач на уровне сервера, например для создания или обработки базы данных, изменения свойств сервера или запуска трассировки (кроме обработки событий), пользователь должен быть членом роли администратора сервера.  
  
 Членство в ролях определяется при установке служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Пользователь, выполняющий программу установки, может добавить себя или другого пользователя к этой роли. Чтобы продолжить установку, необходимо указать хотя бы одного администратора.  
  
 По умолчанию члены локальной группы администраторов автоматически получают права администраторов в службе Analysis Server. Хотя локальной группе явно не предоставлено членство в роли администратора сервера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , локальные администраторы могут создавать базы данных, создавать пользователей и разрешения и выполнять другие разрешенные системным администраторам задачи. Кроме этого, можно настроить неявное предоставление прав администратора. Эта возможность определяется свойством сервера **BuiltinAdminsAreServerAdmins** , имеющим по умолчанию значение **true** . Это свойство вы можете изменить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Security Properties](../../analysis-services/server-properties/security-properties.md).  
  
 После установки можно изменить членство в роли, чтобы добавить дополнительных пользователей с полными правами доступа к службе. Ролями сервера вы можете также управлять с помощью объектов AMO. Дополнительные сведения см. в разделе [Разработка объектов управления аналитикой (объекты AMO)](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предусматривают несколько очень детализированных ролей, позволяющих обрабатывать и выполнять запросы на уровне сервера, базы данных или объекта. Инструкции по использованию этих ролей см. в разделе [Роли и разрешения (службы Analysis Services)](../../analysis-services/multidimensional-models/roles-and-permissions-analysis-services.md).  
  
## Изменение членства в роли сервера  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], в обозревателе объектов щелкните правой кнопкой мыши имя экземпляра и выберите пункт **Свойства**.  
  
2.  На панели **Выбор страницы** щелкните **Безопасность** и нажмите кнопку **Добавить** , расположенную в нижней части страницы, чтобы добавить к роли сервера одного или нескольких пользователей или групп Windows.  
  
     ![Диалоговое окно «Добавление пользователей» в среде Management Studio](../../analysis-services/instances/media/ssas-serveradminadd.png "Диалоговое окно «Добавление пользователей» в среде Management Studio")  
  
### Добавление учетных записей компьютеров  
 С помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] можно сделать учетную запись компьютера участником группы администраторов [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
1.  В диалоговом окне **Выбор пользователей или групп** щелкните **Расположение**.  
  
2.  Выберите домен, к которому принадлежат компьютеры, какие необходимо добавить, или выберите **Весь каталог** и нажмите кнопку **ОК**.  
  
3.  Щелкните **Типы объектов**.  
  
4.  Установите флажок **Компьютеры** и нажмите кнопку **ОК**.  
  
     ![add computer accounts as ssas administrators](../../analysis-services/instances/media/ssas-in-ssms-computerobjects.png "add computer accounts as ssas administrators")  
  
5.  В текстовом поле **Введите имена объектов для выбора** введите имя компьютера и нажмите кнопку **Проверить имена** , чтобы проверить, находится ли учетная запись компьютера в текущем расположении. Если учетная запись компьютера не найдена, проверьте имя компьютера и домена, членом которого является компьютер.  
  
## Учетная запись NT Service\SSASTelemetry  
 **NT Service/SSASTelemetry** — это учетная запись компьютера с ограниченными правами, которая создается во время установки и используется исключительно для реализации службы программы улучшения качества программного обеспечения службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Для выполнения нескольких команд обнаружения этой службе необходимы права администратора на экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Дополнительные сведения см. в разделах [Customer Experience Improvement Program for SQL Server Data Tools](../../sql-server/customer-experience-improvement-program-for-sql-server-data-tools.md) и [Microsoft SQL Server Privacy Statement](../Topic/Microsoft%20SQL%20Server%20Privacy%20Statement.md) .  
  
## См. также раздел  
 [Предоставление доступа к объектам и операциям (службы Analysis Services)](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)   
 [Роли безопасности (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models/olap-logical/security-roles-analysis-services-multidimensional-data.md)  
  
  