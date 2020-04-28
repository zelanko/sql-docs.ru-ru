---
title: Запуск примера приложения адресной книги | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 3a2644e9-d634-4ae6-a5b7-13fb7b317ec7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 45324642d2f323297ecbe091617fbb14cc5fc785
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922246"
---
# <a name="running-the-address-book-sample-application"></a>Выполнение примера приложения адресной книги
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Чтобы запустить приложение адресной книги, выполните следующую процедуру.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-run-this-application"></a>Запуск приложения  
  
1.  Убедитесь, что Microsoft SQL Server работает. Нажмите кнопку **Пуск**, укажите пункт **программы**, выберите **Microsoft SQL Server 7,0**, а затем щелкните **Service Manager**. Если в белом кружке есть зеленая стрелка, то SQL Server выполняется. Если это не так (в белом круге будет красный квадрат), нажмите кнопку **Пуск/продолжить**.  
  
2.  В Microsoft Internet Explorer 4,0 или более поздней версии введите следующий адрес:  
  
     **https://** *webserver* **/РДС/аддрессбук/аддрбук.АСП**  
  
     где веб- *сервер* — имя сервера, на котором установлены компоненты RDS Server.  
  
3.  Затем можно попробовать различные сценарии в примере приложения адресной книги, например поиск человека по его имени, список всех людей с названием «руководитель программы» или изменение существующих записей. Нажмите кнопку **найти** , чтобы заполнить сетку данных всеми доступными именами.  
  
## <a name="see-also"></a>См. также:  
 [Объект привязки данных адресной книги](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)




