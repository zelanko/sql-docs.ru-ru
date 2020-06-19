---
title: Создание Visual Basic проекта SMO в Visual Studio .NET | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic [SMO]
ms.assetid: d7a3892c-0f1c-4c4d-8480-b58dce3720bc
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 49eb94833d10b2e901c008092aea29eab8e4ad48
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84933685"
---
# <a name="create-a-visual-basic-smo-project-in-visual-studio-net"></a>Создание проекта SMO на языке Visual Basic в среде Visual Studio .NET
  В данном разделе описывается, как построить простое консольное приложение командной строки SMO.  
  
 В этом примере импортируются пространства имен, что позволяет программе ссылаться на типы объектов SMO. Импорт пространства имен `Agent` необязателен. Его следует выполнить при написании программы, в которой используется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пространство имен `Common` требуется для установления безопасного соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пространство имен `SqlClient` используется для обработки ошибок, связанных с исключениями SQL.  
  
### <a name="creating-a-visual-basic-smo-project-in-visual-studionet"></a>Создание проекта SMO на языке Visual Basic в среде Visual Studio.NET  
  
1.  Запустите среду [!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] (или [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)]).  
  
2.  В меню **Файл** выберите пункт **Создать проект**. Откроется диалоговое окно **Создание проекта** .  
  
3.  В диалоговом окне **типы проектов** выберите **Visual Basic**, а затем выберите **Windows**. В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] области Установленные шаблоны выберите **консольное приложение.**  
  
4.  Используемых В поле **имя** введите имя нового приложения.  
  
5.  Нажмите кнопку **ОК** , чтобы загрузить [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Шаблон консольного приложения.  
  
6.  В меню **Проект** выберите пункт **Добавить ссылку**. Откроется диалоговое окно **Добавление ссылки**.  
  
7.  Нажмите кнопку **Обзор**, найдите сборки SMO в папке C:\PROGRAM Files\Microsoft SQL Server\120\SDK\Assemblies, а затем выберите следующие файлы. Для построения приложения SMO необходимы как минимум следующие файлы:  
  
     Microsoft.SqlServer.ConnectionInfo.dll  
  
     Microsoft.SqlServer.SqlEnum.dll  
  
     Microsoft.SqlServer.Smo.dll  
  
     Microsoft.SqlServer.Management.Sdk.Sfc  
  
    > [!NOTE]  
    >  Используйте клавишу `Ctrl`, чтобы выбрать несколько файлов.  
  
8.  Добавьте все дополнительные сборки SMO, которые могут потребоваться. Например, если программа предназначена для компонента [!INCLUDE[ssSB](../../includes/sssb-md.md)], добавьте следующие сборки:  
  
     Microsoft.SqlServer.ServiceBrokerEmum.dll  
  
9. Нажмите кнопку **Открыть**.  
  
10. В меню **вид** выберите пункт **код**.-или-выберите окно Module1. vb, чтобы отобразить окно кода.  
  
11. В коде перед любыми объявлениями введите следующие операторы **Imports** , чтобы определить типы в пространстве имен SMO.  
  
    ```  
    Imports Microsoft.SqlServer.Management.Smo  
    Imports Microsoft.SqlServer.Management.Common  
    ```  
  
12. В SMO имеются различные пространства имен в узле Microsoft.SqlServer.Management.Smo, такие как Microsoft.SqlServer.Management.Smo.Agent. Добавьте эти пространства имен при необходимости.  
  
13. Теперь можно добавить свой код SMO.  
  
  
