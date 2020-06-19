---
title: Выбор пакета | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 53b81c8c1ecf6d0399066fee9cdb779d7ac556d2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84918272"
---
# <a name="select-a-package"></a>Выбор пакета
  Используйте диалоговое окно **Выбор пакета** , чтобы указать пакет, из которого задача «Очередь сообщений» может получать сообщения.  
  
## <a name="static-options"></a>Статические параметры  
 **Местоположение**  
 Определяет местонахождение пакета. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Установите местонахождение экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе данного значения отображаются динамические параметры, **Сервер**, **Использовать проверку подлинности Windows**, **Использовать проверку подлинности SQL Server**, **Имя пользователя**и **Пароль**.|  
|Файл DTSX|Установите местонахождение для файла DTSX. При выборе этого значения отображается динамический параметр **Имя файла**.|  
  
## <a name="location-dynamic-options"></a>Динамические параметры местоположения  
  
### <a name="location--sql-server"></a>Местонахождение = SQL Server  
 **Имя пакета**  
 Выберите пакет, хранимый на указанном сервере.  
  
 **Server**  
 Введите имя сервера или выберите его из списка.  
  
 **Использовать проверку подлинности Windows**  
 Выберите для использования проверки подлинности Windows.  
  
 **Использовать проверку подлинности SQL Server**  
 Выберите для использования проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **User name**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введите имя пользователя, которое необходимо использовать для входа на сервер.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите пароль.  
  
### <a name="location--dtsx-file"></a>Местонахождение = файл DTSX  
 **Имя файла**  
 Укажите путь к пакету или нажмите кнопку обзора **(...)** и определите его расположение.  
  
## <a name="see-also"></a>См. также:  
 [Задача «Очередь сообщений»](message-queue-task.md)  
  
  
