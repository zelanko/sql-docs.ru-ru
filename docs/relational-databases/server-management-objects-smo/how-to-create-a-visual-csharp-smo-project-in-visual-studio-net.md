---
title: Создание проекта Visual C# SMO в Visual Studio .NET | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 11fb5e8aec7f61c83ec2b3edecdb3aa027cf2693
ms.sourcegitcommit: f3f83ef95399d1570851cd1360dc2f072736bef6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2019
ms.locfileid: "70148648"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio .NET
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В данном разделе описывается, как построить простое консольное приложение командной строки SMO.  
  
 В этом примере импортируются пространства имен, что позволяет программе ссылаться на типы объектов SMO. Импорт пространства имен **агента** является необязательным. Его следует выполнить при написании программы, в которой используется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для установления безопасного соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]требуется общее пространство имен. Пространство имен **SqlClient** используется для обработки ошибок исключений SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio.NET  
  
1. Запуск Visual Studio
  
2. В меню **файл** выберите пункт **создать** , а затем **проект**.  Откроется диалоговое окно **Создание проекта** .   
  
3. \\ \\ **C#** В области установленные перейдите в раздел шаблоны визуальные окна и выберите Консольное приложение. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]  
  
4. Используемых В текстовом поле **имя** введите имя нового приложения.  

5. Нажмите кнопку **ОК** , чтобы загрузить шаблон консольного приложения.  

6. Следуйте инструкциям по [установке SMO](installing-smo.md) , чтобы установить пакет для ссылки на проект.
  
7. В меню **Вид** выберите пункт **Код**.
    
8. В коде перед оператором Namespace введите следующую инструкцию **using** , чтобы определить типы в пространстве имен SMO:
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. В SMO имеются различные пространства имен в узле Microsoft.SqlServer.Management.Smo, такие как Microsoft.SqlServer.Management.Smo.Agent. Добавьте эти пространства имен при необходимости.  
  
16. Теперь можно добавить свой код SMO.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

