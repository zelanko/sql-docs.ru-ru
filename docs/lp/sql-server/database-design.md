---
layout: HubPage
hide_bc: true
title: 'SQL Server: проектирование баз данных'
description: Ознакомьтесь с функциями SQL Server, позволяющими проектировать базы данных в соответствии с потребностями вашего бизнеса.
ms.topic: hub-page
ms.prod: sql
author: MashaMSFT
ms.author: mathoma
ms.date: 12/15/2018
featureFlags:
- clicktale
ms.openlocfilehash: c08b067a8c92b7fea32b53cd8b14b7ecc13272d0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077244"
---
<div id="main" class="v2">
    <div class="container">
        <ul class="cardsY panelContent featuredContent">
            <li>
                <a href="https://www.microsoft.com/evalcenter/evaluate-sql-server-2019-ctp">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-sql-server.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Попробовать SQL Server 2019 (предварительная версия)</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/get-azure-sql-vm.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Получить виртуальную машину с SQL Server</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a href="/sql/ssms/download-sql-server-management-studio-ssms">
                    <div class="cardSize">
                        <div class="cardPadding">
                            <div class="card">
                                <div class="cardImageOuter">
                                    <div class="cardImage">
                                        <img src="media/index/download-ssms.svg" alt="" />
                                    </div>
                                </div>
                                <div class="cardText">
                                    <span class="likeAnH3">Загрузить SQL Server Management Studio</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </a>
            </li>              
        </ul>
    </div>
    <div class="container">
        <h1>SQL Server: стандарт Структура базы данных</h1>
        <ul class="pivots tabLess">
            <li class="pivotItem" style="display: list-item;" data-id="#products">
                <a href="#products" data-linktype="self-bookmark"></a>
                <ul id="products">
                    <li class="panelItem" data-index="0">
                        <a class="singlePanelNavItem selected" href="#products1" data-linktype="self-bookmark"></a>
                        <ul class="cardsD panelContent singlePanelContent" id="products1" style="margin-top: 0px; display: flex;">
                            <li>
                                <a href="/sql/relational-databases/collations/collation-and-unicode-support/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/collation.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Параметры сортировки</h3>
                                                    <p>Параметры сортировки в SQL Server обеспечивают свойства для правил сортировки, а также для учета регистра и диакритических знаков в ваших данных. Параметры сортировки, используемые с символьными типами данных, такими как char или varchar, указывают кодовую страницу и соответствующие символы, которые могут быть представлены для данного типа данных. </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li> 
                            <li>
                                <a href="/sql/relational-databases/databases/databases/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/databases.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Базы данных</h3>
                                                    <p>База данных в SQL Server состоит из коллекции таблиц, в которой хранится определенный набор структурированных данных. Таблица содержит коллекцию строк, также называемых записями или кортежами, и столбцов, также называемых атрибутами.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li> <li>
                                <a href="/sql/relational-databases/blob/filestream-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/filestream.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Файловый поток</h3>
                                                    <p>Файловый поток позволяет приложениям на основе SQL Server хранить в файловой системе неструктурированные данные, например документы и изображения.  </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/blob/filetables-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/filetable.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Filetable</h3>
                                                    <p>Таблица FileTable позволяет приложению интегрировать свои компоненты хранения и управления данными, а также обеспечивает работу интегрированных служб SQL Server, включая полнотекстовый и семантический поиск, с неструктурированными данными и метаданными.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/graphs/sql-graph-overview/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/sql-graphs.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>График</h3>
                                                    <p>База данных графа представляет собой коллекцию узлов (или вершин) и ребер (или связей). Узел представляет собой сущность (например, лицо или организацию), а ребро — связь между двумя узлами, которые оно соединяет (например, отметки "Нравится" или друзей). </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li> 
                            <li>
                                <a href="/sql/relational-databases/hierarchical-data-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/hierarchy-data.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Иерархические данные</h3>
                                                    <p>Иерархические данные представляют собой набор элементов данных, связанных между собой иерархическими связями. Иерархические связи — это связи, в которых один из элементов данных является родителем другого элемента.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/indexes/indexes/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/indexes.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Индексы</h3>
                                                    <p>Обзор различных типов индексов, которые SQL использует для организации данных. </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/sequence-numbers/sequence-numbers/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/sequence-numbers.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Порядковые номера</h3>
                                                    <p>Последовательность представляет собой определяемый пользователем объект, привязанный к схеме, который формирует последовательность числовых значений в соответствии со спецификацией, с которой эта последовательность создавалась.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/spatial/spatial-data-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/spatial-data.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Пространственные данные</h3>
                                                    <p>Пространственные данные представляют сведения о физическом расположении и форме геометрических объектов. Такими объектами могут быть точки или более сложные объекты, например страны, дороги, озера. </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/stored-procedures/stored-procedures-database-engine/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/stored-procedures.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Хранимые процедуры</h3>
                                                    <p>Хранимая процедура в SQL Server представляет собой группу из одного или нескольких операторов Transact-SQL или ссылку на метод среды CLR Microsoft .NET Framework. Процедуры напоминают конструкции на других языках программирования.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li> 
                            <li>
                                <a href="/sql/relational-databases/tables/tables/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/tables.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Таблицы</h3>
                                                    <p>Таблицы являются объектами, которые содержат все данные в базах данных. В таблицах данные логически организованы в виде строк и столбцов по аналогии с электронной таблицей. Каждая строка представляет собой уникальную запись, а каждый столбец — поле записи.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/track-changes/track-data-changes-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/track-changes.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Отслеживание изменений</h3>
                                                    <p>Обзор двух функций, которые позволяют отслеживать данные: отслеживание измененных данных и отслеживание изменений.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/triggers/logon-triggers/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/triggers.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Триггеры</h3>
                                                    <p>Триггеры позволяют автоматизировать ответ на определенное действие, например вход в систему или команду изменения базы данных. </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>
                            <li>
                                <a href="/sql/relational-databases/views/views/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/views.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>Представления</h3>
                                                    <p>Представление — это виртуальная таблица, содержимое которой определяется запросом.</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li>  
                            <li>
                                <a href="/sql/relational-databases/xml/xml-data-sql-server/">
                                    <div class="cardSize">
                                        <div class="cardPadding">
                                            <div class="card">
                                                <div class="cardImageOuter">
                                                    <div class="cardImage">
                                                        <img src="media/database-design/xml-data.svg" alt="" />
                                                    </div>
                                                </div>
                                                <div class="cardText">
                                                    <h3>XML-данные</h3>
                                                    <p>Обзор действий, которые можно выполнить с типом данных, индексами, коллекциями схем XML и другими элементами. </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </a>
                            </li> 
                                    <li>
                                      <a href="/sql/lp/sql-server/query-data/">
                                          <div class="cardSize">
                                              <div class="cardPadding">
                                                  <div class="card">
                                                      <div class="cardImageOuter">
                                                          <div class="cardImage">
                                                              <img src="media/index/query-data.svg" alt="" /> 
                                                          </div>
                                                      </div>
                                                      <div class="cardText">
                                                          <h3>Данные запросов</h3>
                                                          <p><b>Курсоры, синонимы, написание скриптов, соединения, определяемые пользователем функции, полнотекстовый поиск</b></p>
                                                      </div>
                                                  </div>
                                              </div>
                                          </div>
                                      </a>
                                    </li>
                        </ul>
                    </li>
                </ul>
            </li>
        </ul>
    </div>
</div>
<div class="container centered pageFooter">
        <h2>Оставайтесь с нами</h2>
        <ul class="links">
           <li>
                <a href="https://aka.ms/editsqldocs" data-linktype="external"> Принять участие </a>
            </li>
           <li>
                <a href="https://docs.microsoft.com/sql/sql-server/sql-server-get-help" data-linktype="external"> Получить справку </a>
            </li>
           <li>
                <a href="https://aka.ms/sqldocsfeedback" data-linktype="external"> Оставить отзыв </a>
            </li>
           <li>
                <a href="https://aka.ms/sqldocsurvey" data-linktype="external"> Пройти опрос </a>
            </li>
           <li>
                <a href="https://cloudblogs.microsoft.com/sqlserver/" data-linktype="external">Блог</a>
            </li>
            <li>
                <a href="https://twitter.com/sqldocs" data-linktype="external">Twitter</a>
            </li>
            <li>
                <a href="https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqldatabaseengine&filter=alltypes&sort=lastpostdesc" data-linktype="external">Форум MSDN</a>
            </li>
            <li>
                <a href="https://feedback.azure.com/forums/908035-sql-server" data-linktype="external">Отзывы пользователей</a>
            </li>
        </ul>
    </div>