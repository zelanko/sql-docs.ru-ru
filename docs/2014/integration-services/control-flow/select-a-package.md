---
title: Выбор пакета | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 931a122e188f157a2fbcf32adbf9c6dc420d11f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095485"
---
# <a name="select-a-package"></a>Выбор пакета
  Используйте диалоговое окно **Выбор пакета** , чтобы указать пакет, из которого задача «Очередь сообщений» может получать сообщения.  
  
## <a name="static-options"></a>Статические параметры  
 **Местоположение**  
 Определяет местонахождение пакета. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Описание|  
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
  
 **Имя пользователя**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введите имя пользователя, которое необходимо использовать для входа на сервер.  
  
 **Пароль**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] укажите пароль.  
  
### <a name="location--dtsx-file"></a>Местонахождение = файл DTSX  
 **Имя файла**  
 Укажите путь к пакету или нажмите кнопку обзора **(…)** и определите его расположение.  
  
## <a name="see-also"></a>См. также  
 [Задача «Очередь сообщений»](message-queue-task.md)  
  
  