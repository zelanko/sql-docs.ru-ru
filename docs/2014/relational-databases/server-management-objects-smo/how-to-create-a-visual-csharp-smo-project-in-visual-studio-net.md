---
title: Создание проекта Visual C# SMO в Visual Studio .NET | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: 42
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b96b2f52b1d993c02536b70e39ba7d1868643a04
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100167"
---
# <a name="create-a-visual-c-smo-project-in-visual-studio-net"></a>создание проекта SMO на языке Visual C# в среде Visual Studio .NET
  В данном разделе описывается, как построить простое консольное приложение командной строки SMO.  
  
 В этом примере импортируются пространства имен, что позволяет программе ссылаться на типы объектов SMO. Импорт пространства имен `Agent` необязателен. Его следует выполнить при написании программы, в которой используется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пространство имен `Common` требуется для установления безопасного соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пространство имен `SqlClient` используется для обработки ошибок, связанных с исключениями SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio.NET  
  
1.  Запустите среду [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (или [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  В меню **Файл** выберите пункт **Создать проект**. Откроется диалоговое окно **Создание проекта** .  
  
3.  В **типы проектов** выберите **Visual C#**, а затем выберите **Windows**. В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] выберите установленные шаблоны **приложение Windows**.  
  
4.  (Необязательно) В **имя** введите имя нового приложения.  
  
5.  Выберите тип приложения Visual C#. Примеры, которые следует выполнить, выберите **консольное приложение**.  
  
6.  В меню **Проект** выберите пункт **Добавить ссылку**. Откроется диалоговое окно **Добавление ссылки**.  
  
7.  Нажмите кнопку **Обзор**, найдите сборки SMO в [!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)] папку, а затем выберите следующие файлы. Для построения приложения SMO необходимы как минимум следующие файлы:  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
    > [!NOTE]  
    >  Используйте клавишу `Ctrl`, чтобы выбрать несколько файлов.  
  
8.  Добавьте все дополнительные сборки SMO, которые могут потребоваться. Например, если программа предназначена для компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], добавьте следующие сборки:  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Нажмите кнопку **Открыть**.  
  
10. На **представление** меню, нажмите кнопку **кода**. - или - выберите «Program1.cs [Design] Windows и дважды щелкните форму windows для отображения окна кода.  
  
11. В коде перед инструкцией пространства имен введите следующие инструкции `using` для определения типов в пространстве имен объектов SMO.  
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
12. В SMO имеются различные пространства имен в узле Microsoft.SqlServer.Management.Smo, такие как Microsoft.SqlServer.Management.Smo.Agent. Добавьте эти пространства имен при необходимости.  
  
13. Теперь можно добавить свой код SMO.  
  
  