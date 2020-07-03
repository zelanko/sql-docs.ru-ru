---
title: создание проекта SMO на языке Visual C# в среде Visual Studio .NET
ms.custom: seo-dt-2019
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
ms.openlocfilehash: 60d0f5b55664312be1bdf6501cf54e78a826434b
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85900632"
---
# <a name="how-to-create-a-visual-c-smo-project-in-visual-studio-net"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio .NET
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw.md)]

  В данном разделе описывается, как построить простое консольное приложение командной строки SMO.  
  
 В этом примере импортируются пространства имен, что позволяет программе ссылаться на типы объектов SMO. Импорт пространства имен **агента** является необязательным. Его следует выполнить при написании программы, в которой используется агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Для установления безопасного соединения с экземпляром требуется **Общее** пространство имен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Пространство имен **SqlClient** используется для обработки ошибок исключений SQL.  
  
### <a name="creating-a-visual-c-smo-project-in-visual-studionet"></a>Создание проекта SMO на языке Visual C# в среде Visual Studio.NET  
  
1. Запуск Visual Studio
  
2. В меню **файл** выберите пункт **создать** , а затем **проект**.  Откроется диалоговое окно **Создание проекта** .   
  
3. На панели [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **установки** перейдите в раздел **шаблоны** \\ **Visual C#** \\ **окна** и выберите **консольное приложение**.  
  
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

