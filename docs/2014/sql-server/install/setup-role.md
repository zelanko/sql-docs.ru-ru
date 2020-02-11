---
title: Роль установки | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c7e9db15-89f2-4d4d-8860-1e64c5821c4d
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: b1cf8c6f8442fc69669c10106f671040733e48ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66092224"
---
# <a name="setup-role"></a>Роль установки
  На этой странице можно указать, будет страница «Выбор компонентов» использоваться для выбора отдельных функций или для установки с использованием роли установки.  
  
 
  `setup role` представляет собой фиксированный выбор для всех функций и общих компонентов, которые необходимы для реализации стандартной конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Установка компонентов**  
 Укажите этот параметр для выбора отдельных функций и общих компонентов. В число компонентов экземпляра входят службы Database Engine Services, Analysis Services (в собственном режиме) и Reporting Services.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerPivot для SharePoint**  
 Укажите этот параметр для установки компонентов сервера служб Analysis Services на ферме SharePoint 2010. В этом случае служба PowerPivot System и сервер служб Analysis Services развертываются на ферме, обеспечивая обработку запросов и данных для опубликованных книг Excel, которые содержат внедренные данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 Дополнительно в установку можно включить экземпляр ядра СУБД для реляционных баз данных, если он необходим для размещения баз данных в ферме SharePoint. Если ферма уже настроена, этот шаг можно пропустить.  
  
 После завершения установки необходимо настроить программное обеспечение с помощью одного из следующих подходов: средство настройки PowerPivot, командлеты PowerShell или центр администрирования SharePoint 2010. В отличие от предыдущих выпусков, программа установки больше не выполняет какие-либо задачи по настройке установки PowerPivot.  
  
 Установка на основе роли не включает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot для клиентского приложения Excel. Клиентское приложение устанавливается отдельно.  
  
 **Все компоненты по умолчанию**  
 Выберите эту роль установки, чтобы установить все компоненты, доступные для этой версии. Обратите внимание, что PowerPivot для SharePoint исключен из этой роли. Чтобы установить этот компонент, необходимо использовать роль программы установки PowerPivot для SharePoint.  
  
 Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] настраивается для запуска с использованием учетной записи **NT AUTHORITY\NETWORK SERVICE**. Текущий пользователь подготавливается в качестве члена роли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin**. Значения, заданные этим параметром, могут быть переопределены с помощью дополнительных параметров командной строки.  
  
 Если операционная система не является контроллером домена, по умолчанию в компоненте Database Engine и службах Reporting Services используется учетная запись NTAUTHORITY\NETWORK SERVICE, в Integration Services — учетная запись NTAUTHORITY\NETWORK SERVICE, а в средстве запуска управляющей программы полнотекстовой фильтрации SQL — учетная запись NTAUTHORITY\LOCAL SERVICE.  
  
## <a name="see-also"></a>См. также:  
 [Установка PowerPivot для SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906)   
 [Требования к оборудованию и программному обеспечению (PowerPivot для SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823)   
 [Выбор компонентов](../../../2014/sql-server/install/feature-selection.md)  
  
  
