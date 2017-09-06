---
title: "Развертывание пользовательской сборки | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
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
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
caps.latest.revision: 46
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 44b3944bcef88371e19d01c0e22e5522d62ef645
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="deploying-a-custom-assembly"></a>Развертывание пользовательской сборки
  Чтобы развернуть пользовательскую сборку в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], поместите сборку в эти папки сервера отчетов и конструктора отчетов. По умолчанию, предоставляются пользовательские сборки **выполнения** разрешение в [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Чтобы предоставить пользовательским сборкам права доступа, кроме разрешения Execute, будет необходимо изменить файл конфигурации rssrvpolicy.config для сервера отчетов и файл конфигурации rspreviewpolicy.config для окна предварительного просмотра конструктора отчетов. Также можно установить пользовательскую сборку в глобальный кэш сборок.  
  
> [!NOTE]  
>  Существует два режима предварительного просмотра конструктора отчетов: на вкладке предварительного просмотра и всплывающее окно предварительного просмотра, открывающегося при запуске проекта отчета в **DebugLocal** режим. На вкладке предварительного просмотра выполняются с помощью во всех выражениях отчета **FullTrust** набор разрешений и не применяются параметры политики безопасности. Всплывающее окно предварительного просмотра предназначено для имитации функциональных возможностей сервера отчетов и поэтому имеет файл конфигурации политики, который необходимо изменить (возможно, при участии администратора), чтобы использовать пользовательские сборки в конструкторе отчетов. Это всплывающее окно предварительного просмотра также блокирует пользовательскую сборку. Поэтому для изменения или обновления кода пользовательской сборки необходимо закрыть окно предварительного просмотра.  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a>Развертывание пользовательской сборки в службах Reporting Services  
  
1.  Скопируйте пользовательскую сборку из каталога построения в папку bin на сервере отчетов или в папку конструктора отчетов. По умолчанию папка bin для сервера отчетов находится в %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin. Конструктор отчетов по умолчанию находится в папке %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
     Размещение пользовательской сборки в папке bin сервера отчетов позволяет опубликовывать отчеты, которые ссылаются на пользовательскую сборку, а размещение пользовательской сборки в папке конструктора отчетов позволяет запускать и выполнять отладку отчетов, которые ссылаются на пользовательскую сборку в конструкторе отчетов.  
  
     Чтобы предоставить коду пользовательской сборки разрешения кроме разрешения Execute по умолчанию, выполните следующие действия.  
  
2.  Откройте соответствующий файл конфигурации. Файл rssrvpolicy.config по умолчанию находится в папке %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer. Файл rspreviewpolicy.config по умолчанию находится в папке %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies.  
  
3.  Добавьте группу кода для пользовательской сборки. Дополнительные сведения см. в разделе [разработки безопасного &#40; Службы Reporting Services &#41; ](../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="updating-custom-assemblies"></a>Обновление пользовательских сборок  
 На некотором этапе может понадобиться обновить версию пользовательской сборки, на которую существуют ссылки в нескольких опубликованных отчетах. Если эта сборка уже существует в каталоге bin сервера отчетов или конструктора отчетов и номер версии сборки увеличивается или изменяется иным образом, уже опубликованные отчеты перестанут правильно работать. Вам потребуется обновить версию сборки, которая указывается в **CodeModules** элемент определения отчета и повторно опубликовать отчеты. Если известно, что пользовательская сборка будет часто обновляться, а отчетам, опубликованным в настоящий момент, необходимо ссылаться на новую сборку, рекомендуется использовать одинаковые номера версий для всех обновлений данной сборки.  
  
 Если не нужно ссылаться на новую версию сборки в опубликованных отчетах, можно развернуть пользовательскую сборку в глобальном кэше сборок. Глобальный кэш сборок может хранить несколько версий одной сборки, поэтому текущие отчеты могут ссылаться на предыдущую версию сборки, а вновь публикуемые отчеты — на обновленную сборку. Другим способом является задание перенаправления привязки сервера отчетов, чтобы вызвать принудительное перенаправление всех запросов старой сборки на новую сборку. Для этого необходимо изменить файлы сервера отчета Web.config и ReportService.exe.config. Запись файла конфигурации может иметь следующий вид:  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [Работа со сборками и глобальный кэш сборок](http://go.microsoft.com/fwlink/?LinkId=63912)  
  
  
