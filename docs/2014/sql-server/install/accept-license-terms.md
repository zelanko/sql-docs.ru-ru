---
title: Принять условия лицензионного соглашения | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- license terms
helpviewer_keywords:
- Registration Information page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Registration Information page
ms.assetid: 08dd739d-5817-4418-bcff-74ab7f8bbd33
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 99418b11eecdb3077e3def746eae56e43bab2d60
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096840"
---
# <a name="accept-license-terms"></a>Принятие условий лицензионного соглашения
  На странице **Принять условия лицензии** мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] примите условия лицензии для этого выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Лицензионное соглашение можно распечатать или скопировать в буфер обмена. Чтобы продолжить работу, примите условия лицензии, а затем нажмите кнопку **Далее**. Чтобы закрыть программу установки, нажмите кнопку **Отмена**.  
  
## <a name="customer-experience-improvement-program-ceip"></a>Программа улучшения качества программного обеспечения (CEIP)  
 Если включить отчеты программы улучшения качества программного обеспечения, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет настроен для периодической отправки отчетов в [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Отчеты будут содержать сведения о конфигурации оборудования, а также об использовании [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и его компонентов. Эти данные используются корпорацией [!INCLUDE[msCoName](../../includes/msconame-md.md)] для совершенствования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эта функция отслеживает следующие компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   
  [!INCLUDE[ssDE](../../includes/ssde-md.md)]
  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Репликация  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Установки  
  
 Сведения об использовании функций отправляются в [!INCLUDE[msCoName](../../includes/msconame-md.md)], где хранятся с ограничением доступа.  
  
 Чтобы отключить отчеты программы улучшения качества по после завершения установки, используйте средство ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отчетов об ошибках и использовании** в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]меню **средства настройки** .  
  
 Что же касается таких действий, осуществляемых программой установки, как установка, обновление, исправление и т. д., то сбор и передача сведений о них осуществляется только во время работы программы установки.  
  
 Применительно ко всем прочим компонентам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сбор сведений производится всего один раз в день по всем разрешенным экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. По умолчанию сбор запланирован на полночь, что позволяет свести к минимуму нагрузку на сервер. Если необходимо изменить время сбора данных, можно вручную отредактировать раздел реестра, управляющий этим временем. Каждый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует собственный раздел реестра:  
  
 \\[!INCLUDE[msCoName](../../includes/msconame-md.md)]HKLM\Software\\\MSSQL12.[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceId> \кпе\тимеофрепортинг  
  
 Значение этого раздела реестра содержит время сбора данных как число минут с 00:00 (полуночи) до времени запуска. Например, значение, равное 60, запустит сбор данных в 1:00, значение 1200 — в 20:00, и так далее.  
  
## <a name="error-reporting"></a>Отчет об ошибках  
 Страница **Параметры отчетов об ошибках и использовании** мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет включить для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]функции отправки отчетов об ошибках и использовании.  
  
### <a name="options"></a>Параметры  
 По умолчанию функции сбора данных об использовании компонентов и отчета об ошибках отключены для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и его компонентов в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Отчет об ошибках  
 Если включить функцию отчетов об ошибках, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет настроен для автоматической отправки отчета в [!INCLUDE[msCoName](../../includes/msconame-md.md)] в случае неустранимой ошибки в любом из следующих компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   
  [!INCLUDE[ssDE](../../includes/ssde-md.md)]
  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Субагент  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Репликация  
  
 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] использует отчеты об ошибках, чтобы улучшить функциональность [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и любые поступающие данные расценивает как конфиденциальные.  
  
 Сведения об ошибках отправляются в [!INCLUDE[msCoName](../../includes/msconame-md.md)] по защищенному (HTTPS) соединению и хранятся там с ограничением доступа. Вместо этого отчеты об ошибках можно отправлять на собственный корпоративный сервер отчетов об ошибках.  
  
 Отчеты об ошибках содержат следующие сведения:  
  
-   состояние [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при возникновении проблемы;  
  
-   версия операционной системы и сведения об оборудовании компьютера;  
  
-   код продукта, который не используется для идентификации лицензии;  
  
-   сетевой IP-адрес компьютера или прокси-сервера;  
  
-   данные из памяти или файлов процесса, вызвавшего ошибку.  
  
 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] не собирает преднамеренно файлы, имя, адрес, адрес электронной почты или персональные данные в любой другой форме. Однако в отчет об ошибке из памяти или файлов процесса, вызвавшего ошибку, могут попасть персональные данные. Хотя потенциально эти сведения можно использовать, чтобы идентифицировать пользователя, [!INCLUDE[msCoName](../../includes/msconame-md.md)] не использует их с этой целью.  
  
 Дополнительные сведения о правилах сбора данных и обращения с личными сведениями [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Заявление о конфиденциальности Microsoft SQL Server](../../../2014/getting-started/microsoft-sql-server-privacy-statement.md).  
  
 Если при возникновении неустранимой ошибки отчеты об ошибках включены, в журнале событий Windows могут появиться записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] , в которых содержатся ссылки на соответствующие статьи базы знаний [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 Чтобы отключить отчеты об ошибках или использовании возможностей для всех экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и его компонентов после завершения установки, перейдите в диалоговое окно **Настройки параметров отчета об ошибках и использовании** и снимите флажки для пункта **Использование возможностей**. Если для нескольких компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (общие компоненты [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], и) включены **отчеты об ошибках** , можно отключить отчеты об ошибках для каждого экземпляра отдельного компонента, а также общих компонентов, перечисленных как **другие**.  
  
## <a name="see-also"></a>См. также:  
 [Об условиях лицензионного соглашения SQL Server](../../../2014/getting-started/about-the-sql-server-license-terms.md)  
  
  
