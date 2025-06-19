А) 
"Одной из первых вещей, которая бросилась мне в глаза, стали соглашения по именованию. Думаю, мы могли бы почерпнуть оттуда полезные идеи и определить стандарты, которые подойдут всем. Есть ли у вас документ, где суммированы используемые в проекте соглашения по именованию и стилю кода? Мы могли бы его изучить и либо принять эти стандарты, либо адаптировать часть из них. Такой документ также был бы полезен для новых участников проекта, так как, полагаю, на первых порах эти правила могут вызывать затруднения."

У нас есть внутренний расширенный код стандарт, но сейчас мы его практически не придерживаемся. Есть некоторые вещи, которые ребятам кажутся удобными, но мы готовы писать в вашем стиле, просто скажите, какие у вас приняты конвенции.

Б)
**Более разговорный вариант:**  
"К вопросу о документации - у вас есть права на запись в наш Notion? Было бы здорово, если бы вы могли добавить туда:
- Ваши стандарты именования
- Описание плагинов из вашего списка:
    - Для чего каждый нужен
    - Где искать их реализацию в коде
    - Как их правильно использовать
Это реально помогло бы всем разобраться в проекте быстрее."

Похоже что доступа в кашей документации у нас нет. По крайней мере на мою почту vmukshin@obeliskstd.com ничего не приходило.

В)
**Более разговорный вариант:**  
"Заметил, что у вас GAS задействован для довольно простых вещей. Как бы вы оценили уровень expertise команды Obelisk в работе с этой системой? Хочу понять, насколько ваши наработки можно использовать как обучающий материал.
Было бы классно, если бы вы обозначили:
- Что у вас "прокачано" на 100% и можно смело брать за образец
- Где могут быть "сырые" места, которые нужно дорабатывать или воспринимать как прототип
Это не критика — просто хочу расставить приоритеты при интеграции."

Мы не используем GAS в своих проектах, т.к. он имеет некоторые накладные расходы и не самую эффективную архитектуру. Однако мы знаем, что у вас так же применяется GAS и для упрощения интеграции мы применили его в точках соприкосновения. Но мы не знаем насколько глубоко он используется в вашем проекте, по этому не делали ничего сложного. В текущей реализации мы не были уверены, как будет проходить интеграция, если нужно совместно мы разработаем техническую спецификацию по компонентам GAS с учетом сетевого кода как для наших систем, так и для всего проекта в целом. Это наша достаточно сильная сторона.

Г)
"Ребята, это ваш собственный фреймворк из предыдущего проекта? Система оружия выглядит очень основательной. Как думаете, что нам с ней делать? Какие части точно стоит оставить, а что, может быть, переработать под наши нужды?"

Весь код написан заново. Возможно в условиях неопределенности он немного разросся. Сейчас мы не ставим перед собой задачу сделать все идеально, условия меняются слишком часто и какая часть написанного пойдет в работу не известно. По этому мы пишем так, чтобы это легко переписывалось или выкидывалось.

Д)
"Заметил, что вы, кажется, сделали большую часть фич мультиплеерными (не проверял всё досконально). Как у вас с этим обстоят дела?
У нас пока вообще нет MP-поддержки. Нужно будет с командой решать, как это внедрять - это обязательное требование, но я пока не уверен по срокам (будем делать постепенно), потому что это немного притормозит прототипирование."

К счастью Анриал - мультиплеерный движок, по этому мы пишем так, чтобы все работало. На этапе прототипирования это практически не требует усилий, но если мультиплеер не предусмотреть сразу, архитектура может получиться не корректной.

Е)
"Вижу, что для системы взаимодействий вы используете GAS messaging. Какие плюсы/минусы против интерфейсов (вроде бы они тоже есть в коде, но не используются)? Я в курсе, что это временно, но всё же интересно - почему выбрали именно такой подход?"

Это самое простое решение. Мы ожидаем, что у вас будет своя интерактивная система и все написано так, чтобы просто переключиться на вашу реализацию. Так же мы не знаем как у вас организованна работа с инпутом, по этому использовали GAS message. Исключительно чтобы работало. Этот код не имеет практической ценности.

Ж)
3Д

З)
"Какие 2-3 вещи, по твоему мнению, лучше всего подойдут для начала интеграции?"

1. Нам нужно определить AC для модулей которые мы делаем. 
2. Перед началом интеграции будет здорово ознакомиться с уже существующей архитектурой проекта и его правилами. Возможно формат плагинов не подойдет или у вас какие то вещи организованны не так как у нас. Весь написанный код готов к адаптации под любые нужды, он очень простой, многие вещи можно сделать эффективнее, но это займет больше времени.
3. В целом все модули готовы к первичной интеграции, т.к. они выполнены как плагины, они могут подключаться и отключаться от проекта не затрагивая вашу кодовую базу.

==========================
a) One of the first thing that hit me are the naming conventions. I think we could get some inspiration from that and define something that works for everyone. Do you have a document summarizing the naming and coding conventions you are using in this project so we can go through them and either decide to go with them, or adapt some of them. Also this doc would be helpful for anyone getting started with your project as I guess they may be confusing at first

"We have our own internal extended code standard, but honestly, we barely follow it these days. Some things feel more natural to the team, but we’re totally fine switching to your style—just let us know what conventions you use." (edited)

b) Follow up to a), do you guys have write access to our notion in order to push some documentation (like the naming conventions), but also the list of plugins you shared above, with their purpose and also their entry point / how to, if applicable - that would be really helpful

"Looks like we don’t have access to your docs—at least I haven’t gotten anything to my email (vmukshin@obeliskstd.com)."

с) I noticed you are using GAS for few simple things. How knowledgeable with GAS would you say the Obelisk team is overall? This is just to get an idea of how valuable your implementations with GAS are going to be as learning material. For that same reason it would be very useful (at least to me), to know what you guys feel very confident about (meaning we can 100% rely on your implementation as learning material and guidance), vs what you think may be weaker areas that may require extra care before integration or should only be taken as prototype and not necessarily proper/clean implementation. Both are fine, it's just good to get your opinion on that to be able to take the necessary actions.

We don't use GAS in our own projects because of its overhead and suboptimal architecture. However, we know you guys use GAS too, so we implemented it at the integration points to make things easier. That said, we weren't sure how deep your GAS implementation goes, so we kept our implementation simple.

d) Did you bring in some framework from your game? The weapon framework seems pretty big. I'm wondering what we can/should do with that in your opinion.

The entire codebase was rewritten from scratch. With all the uncertainty, it might have gotten a bit bloated. We're not aiming for perfection right now – requirements change too often, and who knows what parts will actually make it into production. That's why we're writing everything to be easily refactored or thrown away.

e) More of a remark, it seems that you tried (I couldn't test everything in depth) to get most features working in multiplayer. What can you tell us about that? Right now our project is not going to work in MP at all. I will plan to discuss that with the team and see how we're going to move forward with that because this is definitely a requirement that everything works in MP, I'm just not quite sure yet when we'll be ready to tackle that (probably going to happen over time) - since this is likely going to slow down the prototyping and exploration process a bit.

Unreal is a multiplayer engine at its core, so we're building everything with MP support from the start. During prototyping, this adds almost no extra work – but if you don't design for multiplayer upfront, your architecture will likely end up broken.

f) I saw you are using the GAS messaging system for the interaction system. What can you tell about that? pro/cons with using an interface (which I believe is there too but not used?). I understand this is temporary, as you mentioned earlier, but curious about your feedback.

This is the simplest solution. We expect you'll have your own interaction system, so everything's written to easily switch to your implementation. We also didn't know how you handle input, which is why we used GAS messages - just to make it work. This code has no real practical value.

g) - 3D -

e) What are the 2-3 things you think would be the best candidates for starting the integration?
1. We need to define acceptance criteria (AC) for the modules we're developing.
2. Before integration starts, it would be great to:
	- Review the project's existing architecture and conventions
	- Verify if the plugin format works for you (some approaches might differ from ours)  
    * All code is designed for easy adaptation - it's intentionally simple. Many components could be optimized further, but that would require more time.
3. All modules are integration-ready:
	- Built as standalone plugins
	- Can be enabled/disabled without touching your core codebase

i) Is there anything you need from us at the moment?

Нам бы действительно не помешало получить более конкретное задание по качеству и скорости исполнения задач, возможно об особенностях исполнения и о том, как они будут существовать во основном проекте.