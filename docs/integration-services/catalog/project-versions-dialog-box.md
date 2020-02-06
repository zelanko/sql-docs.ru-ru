---
title: Диалоговое окно "Версии проекта" | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.isprojectprop.versions.f1
ms.assetid: a48a387c-2e70-45bc-be2e-26e57a9bb2c4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9b1715b517f6933a9f904b17ff268fdf7162464d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71294900"
---
# <a name="project-versions-dialog-box"></a>Диалоговое окно «Версии проекта»

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Диалоговое окно **Версии проекта** используется для просмотра версий проекта и восстановления предыдущей версии.  
  
 Можно также просмотреть предыдущие версии в представлении [catalog.object_versions (база данных SSISDB)](../../integration-services/system-views/catalog-object-versions-ssisdb-database.md) и использовать хранимую процедуру [catalog.restore_project (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-restore-project-ssisdb-database.md) для восстановления предыдущих версий.  
  
 **Выбор действия**  
  
-   [Открытие диалогового окна «Версии проекта»](#open_dialog)  
  
-   [Восстановление версии проекта](#restore)  
  
##  <a name="open_dialog"></a> Открытие диалогового окна «Версии проекта»  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Другими словами, подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , размещающего базу данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Для отображения узла **SSISDB** разверните узел **Каталоги служб Integration Services** .  
  
4.  Узел **SSISDB** содержит одну или несколько папок, в каждой из которых содержится один или несколько проектов. Разверните папку, содержащую интересующий вас проект.  
  
5.  Щелкните правой кнопкой мыши проект и выберите пункт **Версии**.  
  
 В диалоговом окне **Версии проекта** в таблице **Версии** отображается список версий проектов, которые развернуты на сервере, с указанием даты и времени развертывания версии и ее восстановления (если таковое имело место), описания версии и ее идентификатора. Активная в настоящее время версия отмечена галочкой в столбце **Текущая** таблицы.  
  
##  <a name="restore"></a> Восстановление версии проекта  
 Для восстановления предыдущей версии проекта выберите версию в таблице **Версии** и щелкните **Восстановление до выбранной версии**. Проект восстанавливается до выбранной версии, которая отмечена флажком в столбце **Текущая** таблицы **Версии** .  
  
  
