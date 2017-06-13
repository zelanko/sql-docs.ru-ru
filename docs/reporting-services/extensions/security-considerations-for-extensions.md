---
title: "Вопросы безопасности для расширений | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- security [Reporting Services], extensions
- extensions [Reporting Services], security
- permissions [Reporting Services], extensions
ms.assetid: 58cbdfeb-1105-4a7d-a3b8-b897ff95f367
caps.latest.revision: 30
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: c7e953f9beea75f08e6c87a210975172e5768d68
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="security-considerations-for-extensions"></a>Вопросы безопасности для модулей
  Все приложения, предназначенные для работы в среде CLR, должны взаимодействовать с системой безопасности этой среды. Такое приложение после вызова на выполнение автоматически проверяется средой CLR и получает от CLR набор разрешений. В зависимости от полученных разрешений приложение либо продолжает свою работу, либо вырабатывает исключение безопасности. Разрешения для кода, получаемые сборкой, определяются локальными параметрами безопасности и политиками в файлах конфигурации политики безопасности для конкретного сервера отчетов.  
  
 Прежде чем запрашивать разрешения, необходимо определить, какие ресурсы и защищенные операции намечено использовать в коде модуля, а также знать о том, какие разрешения применяются для защиты этих ресурсов и операций. Кроме того, необходимо следить за всеми ресурсами, доступ к которым получают любые методы библиотеки классов, вызываемые компонентами модуля. Дополнительные сведения см. в разделе «Запрос на разрешения» документа «Руководство разработчика [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]».  
  
 Модули, развернутые на сервере отчетов необходимо запустить как полностью доверенные это означает, что модуль должен быть частью группы кода, который предоставляется **FullTrust** набор разрешений. Это также означает, что модуль может иметь доступ к определенным ресурсам и операциям сервера, предоставляемым средой CLR, в зависимости от того, какой пользователь прошел проверку подлинности для работы с конкретным отчетом. Дополнительные сведения о группах и пользователях см. в разделе [управления доступом для кода в службах Reporting Services](../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md).  
  
> [!IMPORTANT]  
> В службе  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] принудительно применяется режим безопасности [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для всех собственных модулей.  
  
 При развертывании модулей обработки данных, доставки, подготовки к отображению и безопасности службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] должны соблюдаться следующие условия:  
  
-   Разрешение на развертывание модуля имеет только местный администратор.  
  
-   Файлы конфигурации для расширяемого компонента [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] могут изменять только пользователи с соответствующими разрешениями на чтение и запись.  
  
-   Изменять файлы политики безопасности и включать управление доступом для модуля разрешается только привилегированным пользователям.  
  
 Дополнительные сведения о безопасности доступа к коду в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], в разделе [разработки безопасного &#40; Службы Reporting Services &#41; ](../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
 Дополнительные сведения о средствах безопасности [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] см. в разделе «Безопасность .NET Framework» документа «Руководство разработчика [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]».  
  
## <a name="initialization-of-extension-assemblies"></a>Инициализация сборок модуля  
 При первоначальной загрузке сервером отчетов модулей в память в них используются учетные данные этой службы, поскольку некоторым сборкам модулей требуются специальные разрешения для доступа к системным ресурсам, чтения файлов конфигурации и загрузки других, зависимых сборок. Но после загрузки и инициализации сборки все последующие вызовы сборок модуля осуществляются с использованием учетных данных пользователя, который в данный момент зарегистрирован в системе.  
  
## <a name="see-also"></a>См. также:  
 [модули служб Reporting Services](../../reporting-services/extensions/reporting-services-extensions.md)   
 [Библиотека служб Reporting Services расширения](../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
