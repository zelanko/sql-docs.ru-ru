---
title: Удаленной обработки (службы Analysis Services) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e59011361e6dad623fa5f5cab71d262eb5eb8338
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="remote-processing-analysis-services"></a>Удаленная обработка (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Можно выполнять запланированную или автоматическую обработку на удаленном экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , при этом запрос на обработку приходит с одного компьютера, но выполняется на другом компьютере из той же сети.  
  
## <a name="prerequisites"></a>Предварительные требования  
  
-   Если на каждом компьютере запущены разные версии SQL Server, то клиентские библиотеки должны иметь ту же версию, что и экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , обрабатывающий модель.
  
-   На удаленном сервере должна быть включена функция **Разрешить удаленные соединения с данным компьютером** , а учетная запись, выдающая запрос на обработку, должна быть в списке разрешенных пользователей.  
  
-   Правила брандмауэра Windows должны разрешать входящие соединения с [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Проверьте возможность подключения к удаленному экземпляру [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. См. раздел [Настройка брандмауэра Windows на разрешение доступа к службам Analysis Services](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).  
  
-   Устраните все ошибки локальной обработки перед попыткой проведения удаленной обработки. Проверьте, чтобы при получении локального запроса на обработку данные успешно извлекались из внешнего реляционного источника данных. Инструкции по настройке учетных данных для получения данных см. в разделе [Задание параметров олицетворения (службы SSAS — многомерные)](../../analysis-services/multidimensional-models/set-impersonation-options-ssas-multidimensional.md).  
  
## <a name="on-demand-remote-processing"></a>Удаленная обработка по запросу  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]принимает запросы на обработку от учетных записей пользователя или приложения, имеющие [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] разрешения администратора. Если вы являетесь администратором, проверьте возможность подключения к удаленному экземпляру и обработайте базу данных вручную через удаленное соединение.  
  
1.  На компьютере, который будет использоваться для планирования обработки, запустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и подключитесь к удаленному экземпляру [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Щелкните правой кнопкой мыши базу данных, выберите команду **Обработать**, переведите указатель мыши на **Скрипт** и выберите **Действие со скриптом в новом окне запросов**. В окне запроса появятся команды для начала обработки.  
  
3.  Нажмите кнопку **ОК** , чтобы начать обработку.  
  
     Успешное завершение данной задачи приведет к получению XMLA-запроса, который можно внедрить в запланированное задание. Также это подтверждает, что нет никаких проблем с соединением.  
  
## <a name="schedule-remote-processing-using-sql-server-agent-service"></a>Планирование удаленной обработки с помощью службы агента SQL Server  
 По умолчанию служба агента SQL Server запускается для виртуальной учетной записи с сетевыми подключениями, созданными с помощью учетной записи машины. Чтобы не давать административные права учетной записи машины на удаленном экземпляре [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , следует сменить параметры учетной записи службы агента SQL Server так, чтобы она выполнялась как учетная запись пользователя домена с наименьшими привилегиями.  
  
 Проверьте, чтобы были предоставлены все необходимые разрешения, включая права **sysadmin** , для экземпляра Database Engine, где выполняется служба.  
  
 Используйте следующие ссылки для указания разрешений:  
  
-   [Настройка агента SQL Server](http://msdn.microsoft.com/library/2e361a62-9e92-4fcd-80d7-d6960f127900)  
  
-   Если предоставление разрешений[SQL Server Agent Components](http://msdn.microsoft.com/library/8d1dc600-aabb-416f-b3af-fbc9fccfd0ec) не поддерживается, **SQL Server Agent Components** предлагает альтернативные предопределенные роли сервера.  
  
 После настройки разрешений учетной записи выполните следующие действия.  
  
#### <a name="grant-the-sql-server-agent-account-administrator-permission-on-ssas"></a>Предоставьте учетной записи агента SQL Server разрешения администратора на службы SSAS.  
  
1.  Используя среду [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], подключитесь к удаленному экземпляру [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
2.  Щелкните правой кнопкой мыши имя сервера и выберите пункт**Свойства**, а затем **Безопасность**.  
  
3.  Нажмите кнопку **Добавить** , чтобы добавить учетную запись агента SQL Server.  
  
#### <a name="create-the-job"></a>Создание задания  
  
1.  В среде Management Studio подключитесь к локальному экземпляру Database Engine. Агент SQL Server будет показан в обозревателе объектов как последний элемент списка. При необходимости запустите службу.  
  
2.  Щелкните правой кнопкой мыши узел **Задание**, выберите пункт **Создать** и введите имя.  
  
3.  В мастере нажмите **Создать** и введите имя.  
  
4.  В поле "Тип" выберите **Команда служб SQL Server Analysis Services**.  
  
5.  В поле "Сервер" введите имя удаленного экземпляра [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
6.  В поле "Команда" вставьте XMLA-команду для обработки базы данных. Это XMLA-скрипт, сформированный на предыдущем шаге проверки удаленной обработки по запросу. Нажмите кнопку **ОК** , чтобы сохранить задание.  
  
#### <a name="start-sql-server-profiler"></a>Запуск приложения SQL Server Profiler  
  
1.  На удаленном компьютере запустите приложения SQL Server Profiler. Подключитесь к экземпляру [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] и нажмите **Запуск** , чтобы начать трассировку со стандартными событиями.  
  
     Приложение SQL Server Profiler позволяет отслеживать события обработки в реальном времени.  
  
2.  Дополнительно можно задать свойства трассировки так, чтобы события сохранялись в файл или таблицу базы данных.  
  
#### <a name="run-the-job"></a>Запуск задания  
  
1.  На компьютере, где запускается задание, проверьте, может ли задание выполнить базовую операцию. В обозревателе объектов агента SQL Server разверните узел **Задания**, щелкните правой кнопкой мыши только что созданное задание и выберите команду **Запустить задание по этапам**. Задание будет запущено немедленно. Ход его выполнения можно наблюдать в приложении SQL Server Profiler.  
  
2.  В качестве последнего шага измените задание так, чтобы оно выполнялось по вашему расписанию, добавив необходимые предупреждения и уведомления. Также, возможно, потребуется доработать скрипт обработки или создать несколько этапов в задании, чтобы объекты обрабатывались независимо.  
  
## <a name="see-also"></a>См. также  
 [Компоненты агента SQL Server](http://msdn.microsoft.com/library/8d1dc600-aabb-416f-b3af-fbc9fccfd0ec)   
 [Планирование задач администрирования служб SSAS с помощью агента SQL Server](../../analysis-services/instances/schedule-ssas-administrative-tasks-with-sql-server-agent.md)   
 [Пакетная обработка & #40; Службы Analysis Services & #41;](../../analysis-services/multidimensional-models/batch-processing-analysis-services.md)   
 [Обработка многомерной модели (службы Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Обработка объектов & #40; XML для Аналитики & #41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/processing-objects-xmla.md)  
  
  
