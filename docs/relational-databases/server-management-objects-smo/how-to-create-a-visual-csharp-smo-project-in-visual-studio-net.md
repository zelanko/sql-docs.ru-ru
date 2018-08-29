---
title: Создать проект Visual C# SMO в Visual Studio .NET | Документация Майкрософт
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: smo
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Visual C# [SMO]
ms.assetid: 1e7abb16-23a0-4a18-91ad-253261e6bf84
caps.latest.revision: 43
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3b996e89da78625f6b41f51976329f2779d7a8c5
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43097831"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio .NET
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  В данном разделе описывается, как построить простое консольное приложение командной строки SMO.  
  
 В этом примере импортируются пространства имен, что позволяет программе ссылаться на типы объектов SMO. Импорт **агента** пространства имен является необязательным. Его следует выполнить при написании программы, в которой используется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Распространенных** пространства имен, необходимые для безопасного подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **SqlClient** пространства имен используется для обработки ошибки исключения SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio.NET  
  
1. Запустите Visual Studio
  
2. На **файл** меню, щелкните **New** и затем **проекта**.  Откроется диалоговое окно **Создание проекта** .   
  
3. В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **установленные** панели перейдите к **шаблоны**\\**Visual C#**\\**Windows** и выберите **консольное приложение**.  
  
4. (Необязательно) В **имя** текстовое поле, введите имя нового приложения.  

5. Нажмите кнопку **ОК** загрузить шаблон консольного приложения.  

6. Следуйте инструкциям на [Установка SMO](installing-smo.md) для установки пакета для проекта для ссылки.
  
7. В меню **Вид** выберите пункт **Код**.
    
8. В коде перед инструкцией пространства имен, введите следующую команду **с помощью** инструкции, чтобы уточнить типы в пространстве имен объектов SMO:
  
    ```  
    using Microsoft.SqlServer.Management.Smo;  
    using Microsoft.SqlServer.Management.Common;  
    ```  
  
15. В SMO имеются различные пространства имен в узле Microsoft.SqlServer.Management.Smo, такие как Microsoft.SqlServer.Management.Smo.Agent. Добавьте эти пространства имен при необходимости.  
  
16. Теперь можно добавить свой код SMO.  
  
  
