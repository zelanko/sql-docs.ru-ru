---
title: "Диспетчер подключений Hadoop | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: connection-manager
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ssis.designer.hadoopconn.f1
ms.assetid: 8bb15b97-9827-46bc-aca6-068534ab18c4
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 79b0782d0d01733f10310f1eaac611fc688dbf21
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="hadoop-connection-manager"></a>Диспетчер подключений Hadoop
  Диспетчер подключений Hadoop позволяет пакету служб SSIS подключаться к кластеру с помощью значений, задаваемых для свойств.  
  
## <a name="configure-the-hadoop-connection-manager"></a>Настройка диспетчера подключений Hadoop  
  
1.  В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **Hadoop**и щелкните **Добавить**. Будет открыто диалоговое окно **Редактор диспетчера соединений Hadoop** .  
  
2.  Выберите вкладку **WebHCat** или **WebHDFS** в области слева, чтобы настроить соответствующие сведения о кластере Hadoop.  
  
3.  Если вы включили параметр **WebHCat** для вызова задания Hive или Pig в Hadoop, выполните следующие действия.  
  
    1.  Для параметра **WebHCat Host**(Узел WebHCat) укажите сервер, на котором размещена служба WebHCat.  
  
    2.  Для параметра **WebHCat Port**(Порт WebHCat) укажите порт службы WebHCat (по умолчанию — 50111).  
  
    3.  Выберите метод **аутентификации** доступа к службе WebHCat. Доступные значения: **Обычная** и **Kerberos**.  
  
         ![Редактор диспетчера соединений Hadoop с обычной проверкой подлинности](../../integration-services/connection-manager/media/hadoop-cm-basic.png "редактор диспетчера соединений Hadoop с обычной проверкой подлинности")  
  
         ![Редактор диспетчера соединений Hadoop с проверкой подлинности Kerberos](../../integration-services/connection-manager/media/hadoop-cm-kerberos.png "Hadoop редактор диспетчера соединений с проверкой подлинности Kerberos")  
  
    4.  Для параметра **WebHCat User**(Пользователь WebHCat) укажите **пользователя** с правом доступа к WebHCat.  
  
    5.  Если вы выбрали аутентификацию **Kerberos** , введите **пароль** и **домен**пользователя.  
  
4.  Если вы включили параметр **WebHDFS** для копирования данных из файловой системы HDFS или в нее, выполните следующие действия.  
  
    1.  Для параметра **WebHDFS Host**(Узел WebHDFS) укажите сервер, на котором размещена служба WebHDFS.  
  
    2.  Для параметра **WebHDFS Port**(Порт WebHDFS) укажите порт службы WebHDFS (по умолчанию — 50070).  
  
    3.  Выберите метод **аутентификации** доступа к службе WebHDFS. Доступные значения: **Обычная** и **Kerberos**.  
  
    4.  Для параметра **WebHDFS User**(Пользователь WebHDFS) укажите пользователя с правом доступа к HDFS.  
  
    5.  Если вы выбрали аутентификацию **Kerberos** , введите **пароль** и **домен**пользователя.  
  
5.  Нажмите кнопку **Проверить подключение** для проверки подключения. (Проверяется только включенное вами подключение.)  
  
6.  Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .  
  
## <a name="see-also"></a>См. также  
 [Задача Hadoop Hive](../../integration-services/control-flow/hadoop-hive-task.md)   
 [Задача Pig для Hadoop](../../integration-services/control-flow/hadoop-pig-task.md)   
 [Задача файловой системы Hadoop](../../integration-services/control-flow/hadoop-file-system-task.md)  
  
  

