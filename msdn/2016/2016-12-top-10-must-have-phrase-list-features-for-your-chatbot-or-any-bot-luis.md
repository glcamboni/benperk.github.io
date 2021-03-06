# Top 10 must have Phrase List Features for your chatbot or any bot LUIS

If you haven’t already read my other posts on creating my #chatbot, then check them out:

+ Create a Bot using an Azure App Service Bot Service
+ Most common chatbot questions and how to answer them
+ Publishing a chatbot using Bot Services and LUIS
+ How I tested / debugged my chatbot that I created using the Bot Services on Azure
+ How my chatbot remained statefull using Azure Bot Services
+ C# Bot Builder Samples on GitHub
+ Top 10 must have Phrase List Features for your chatbot or any bot LUIS
+ 1000 must have utterances for your chatbot using LUIS
+ Adding LUIS Entities to my chatbot
+ How I improved my chatbot

Anyway, in a post I am currently working on (How I improved my chatbot) I cover how I decided to create my LUIS entities.  Although the entities were good and they helped my chatbot #chatbot answer or respond to questions better, there are still some words missing.  So I looked for synonyms for my entities, shown in Figure 1 and added the synonymous.

![LUIS entities for a #chatbot][FIGURE1]

###### Figure 1, LUIS entities for a #chatbot

Here is a table that contains the Phrase List for each of the Entities.

| Entity	| Phrases |
| ------- | ------- |
| Bad	| amiss,atrocious,coarse,contaminated,contemptible,corrupt,crappy,cruddy,crummy,defective,deficient,deplorable, depraved,disagreeable,dismal,dissatisfactory,evil,execrable,faulty,foul,ghastly,grungy,harmful,heinous,icky, improper,infamous,inferior,injurious,junky,lousy,nasty,nefarious,off,poor,quality,putrid,rotten,scandalous,sinful,sinister,snide,spoiled,substandard,tainted,thepits,uncouth,wicked |
| Interesting	| absorbing,alluring,animating,appealing,arresting,attractive,beckoning,bewitching,bright,captivating,challenging,consuming,covetable,curious,enchanting,engaging,entertaining,enthralling,enticing,exciting,fascinating,fetching,inspiring,intriguing,inviting,involving,lively,mesmeric,moving,piquant,prepossessing,provocative,spellbinding,spirited,tantalizing,tempting |
| Smart	| alert,analytic,astute,brainy,bright,brilliant,canny,cerebral,cleareyed,clearsighted,clever,creative,cunning,deductive,deft,discerning,eggheaded,enlightened,exceptional,fast,genius,hardboiled,hardheaded,heady,hyperintelligent,imaginative,ingenious,inspired,intellectual,intelligent,inventive,judicious,keen,keenwitted,knowing,logical,nimble,percipient,perspicacious,pointed,prehensile,profound,quick,quickwitted,resourceful,sagacious,sage,sapient,savvy,sharp,sharpwitted,shrewd,sophisticated,supersmart,syllogistic,ultrasmart,versed,wise |
| Boring	| arid,banal,bromidic,characterless,colorless,commonplace,drab,drag,drudging,flat,hackneyed,humdrum,insipid,interminable,irksome,lame,lifeless,monotonous,motheaten,mundane,nothing,platitudinous,prosaic,repetitious,routine,shopworn,spiritless,stale,stereotyped,stodgy,tame,tedious,threadbare,tiresome,tiring,trite,unexciting,uninteresting,unvaried,vapid,wearisome,wellworn, hohum |
| Good	| A1,accomplished,allset,best,certified,champion,choicest,crowning,distinct,excellent,exceptional,exemplary,exquisite,extraordinary,fine,finest,first,firstclass,firstgrade,firstrate,fit,foremost,great,greatest,high,highquality,incomparable,invaluable,magnificent,marvelous,matchless,meritorious,notable,noted,noteworthy,outstanding,peculiar,peerless,phenomenal,piked,premium,priceless,prime,pukka,ready,remarkable,secondtonone,select,shipshape,singular,sound,star,sterling,striking,superb,superior,superlative,supreme,tiptop,topgrade,topnotch,transcendent,unique,unmatched,unprecedented,unusual,worldclass,worthy |
| Important	| important,central,considerable,constitutional,critical,elementary,eminent,especial,essential,foundational,fundamental,indispensable,inherent,intrinsic,main,necessary,needful,particular,primary,principal,required,requisite,significant,special,specific,substantial,underlying,valuable,vital |
| Unsure	| questionable,ambivalent,arguable,debatable,doubtful,dubious,farfetched,improbable,inconclusive,indecisive,indefinite,irresolute,moot,noncommittal,onthefence,open,problematic,suspicious,uncertain,unconvinced,undecided,unproven,unresolved,unsure |
| Irrelevant	| casual,idle,immaterial,inconsequential,inconsiderable,indifferent,insignificant,insubstantial,invalid,light,little,lowranking,meaningless,minor,negligible,nonessential,nugatory,ofnoaccount,ofnoconsequence,paltry,petty,picayune,secondrate,superficial,trifling,trivial,unimportant,unnecessary,useless,worthless,irrelevant,beside |
| Certain	| assured,clear,confident,ofcourse,definite,determined,distinct,inescapable,inevitable,byallmeans,obvious,positive,proved,righton,safebet,sure,unavoidable,undoubted,without,fail |
| Stupid	| dumb,brainless,careless,cloudy,colorless,doltish,dopey,drab,dull,dullwitted,humdrum,idiotic,illadvised,illconceived,illconsidered,illfounded,illjudged,illogical,imbecilic,implausible,inane,lackluster,mindless,moronic,muddled,nonsensical,obtuse,pointless,senseless,shortsighted,silly,simple,simpleminded,slow,stodgy,stupid,trivial,uninspired,unintelligent,unreasonable,unthinking,witless |

Then when I entered an utterance with a word that is in the LUIS Phrase List, it gets recognized in the window automatically, as shown in Figure 2.

![LUIS chatbot utterance with Phrase List content automatically identified][FIGURE2]
###### Figure 2, LUIS chatbot utterance with Phrase List content automatically identified

If you look at the JSON output of the same question you see, that shown below.

```
{
  "query": "You have accomplished a lot",
  "topScoringIntent": {
    "intent": "None",
    "score": 0.489181966
  },
  "intents": [
    {
      "intent": "None",
      "score": 0.489181966
    },
    {
      "intent": "State",
      "score": 0.304426521
    },
    ...
  ],
  "entities": [
    {
      "entity": "accomplished",
      "type": "Good",
      "startIndex": 9,
      "endIndex": 20,
      "score": 0.9996033
    }
  ]
}
```

I can use both the Intent=None and Intent=State as the probabilities are high, the Entity Type: Good and the Entity entity: accomplished to provide a valid and quality response.

Now let’s go code some more stuff!  #AI #ArtificialIntelligence #Cognitive #BotServices #Azure


[FIGURE1]: ../images/2016/msdn-1038.png "Figure 1, LUIS entities for a #chatbot"
[FIGURE2]: ../images/2016/msdn-1038.png "Figure 2, LUIS chatbot utterance with Phrase List content automatically identified"
