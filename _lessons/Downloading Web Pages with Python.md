---
layout: page
title: Downloading Web Pages with Python
description: This lesson teaches how to use python download and extra data---
---

## Source ##
[Turkel, W. J., &amp; Crymble, A. (2012, July 17). Downloading web pages with python. Programming Historian. Retrieved October 3, 2022. doi:https://doi.org/10.46430/phen0021](https://programminghistorian.org/en/lessons/working-with-web-pages)
## Reflection ##
This is a introductionary level lesson and teaches people how to download website information with python. I believe while it is easy lesson to take, we should not underestimated the importance of this lesson part since most of the information are now stored in websites. We cannot accesss and analyze textual evidence without the help of grabing website information. In the lesson, we learnt that there are different types of websites in terms of thier structures, and there might involved various way to retrive their information. In the example link, the website used Java Server Pages (JSP), a server-side programming technology. We extract its information using the packages called urllib in Python. 

After grabed websites information, I wonder whether I can filter out unnecessaty information and only look at those paragraphs in the website. Therefore, I begun to googl ways to extract paragraph information from a XML file. To achive this goal, I used a package called BeautifulSoup to parse the text web info and extract only texts surrounded by the \<p> notation. I attached this practice in this post later as well.

This technique is very important becasue it allows us to have access to a large amount of online resources with simple commands in python and store them locally.

## Code ##
## Preparing the Web Link to Download ##


```python
#the following code reads in first 300 character in the following url
import urllib.request, urllib.error, urllib.parse
from bs4 import BeautifulSoup

url = 'http://www.oldbaileyonline.org/browse.jsp?id=t17800628-33&div=t17800628-33'

response = urllib.request.urlopen(url)
webContent = response.read().decode('UTF-8')
```

## Download File to Local ##


```python
# the following save the webpage to a local html. 
import urllib.request, urllib.error, urllib.parse

url = 'http://www.oldbaileyonline.org/browse.jsp?id=t17800628-33&div=t17800628-33'

response = urllib.request.urlopen(url)
webContent = response.read().decode('UTF-8')

f = open('obo-t17800628-33.html', 'w')
f.write(webContent)
f.close
```




    <function TextIOWrapper.close()>



## Preprocessing with BeautifulSoup ##
BeautifulSoup is a Python library for pulling data from XML and HTML. We find all the information stored in the paragraphs with the function **soup.find_all("p")**. The following output is the extracted text.


```python
# use = BeautifulSoup to extract all the text information from the website
soup = BeautifulSoup(webContent, 'html.parser')
data = ''
for data in soup.find_all("p"):
    print(f'{data.get_text()}')
```

    324.                                                        BENJAMIN                      BOWSEY                                                                                                          (a blackmoor                  ) was indicted for                                                          that he together with five hundred other persons and more, did, unlawfully, riotously, and tumultuously assemble on the 6th of June                      to the disturbance of the public peace and did begin to demolish and pull down the dwelling house of                                                                          Richard                            Akerman                                                                                                                                                            , against the form of the statute, &c.                           
                        ROSE                   JENNINGS                                                                                       , Esq. sworn.
    Had you any occasion to be in this part of the town, on the 6th of June in the evening? - I dined with my brother who lives opposite Mr. Akerman's house. They attacked Mr. Akerman's house precisely at seven o'clock; they were preceded by a man better dressed than the rest, who went up to Mr. Akerman's door; he rapped three times, and I believe pulled the bell as often. Mr. Akerman had barrocadoed his house. When the man found that no one came, he went down the steps, made his obeisance to the mob, and pointed to the door, and then retired.
    Have you any recollection how that man who you say had a better appearance than the rest was dressed? - I think he had on a dark brown coat and a round ha, but I cannot be particular as to that; the mob immediately following in that formidable manner made such an impression upon me, that I did not take notice. The mob approached about thirty in number, three a-breast, some with paving mattocks, others with iron crows and chissels; and then followed an innumerable company with bludgeons; they seemed to be the spokes of coach-wheels; they divided, some went to Mr. Akerman's door with the mattocks, some to the felons door, and some to the debtor's door. I was struck with the formidable appearance and order in which they divided and proceeded to destroy the place, the men threw their sticks up at the windows, which they broke and demolished, yet notwith standing these sticks were coming down in showers, two men with a bar, such as brewers servants carry on their shoulders,See original attacked the parlour window to force it open. The window-shutters were exceedingly tough; they at last forced them partly open, but not quite. I then saw a man in a sailor's jacket helped up, he forced himself neck and heels into the window. They found the house-door still difficult to get open; before it was got open the other parlour window was opened and the mob were throwing the goods out at the window; at last the house-door gave way; about the same time some of the goods and furniture having been thrown out into the street, a fire was kindled.
    They proceeded immediately to throw the goods out of the house? - Immediately. An equal degree of activity seemed to exhibit itself on the outside as within, one party to burn, the other to throw out the goods of Mr. Akerman. When the conflagration took place I applied my mind to the mob.
    Was Mr. Akerman's house on fire then? - No. I was situated in the one-pair-of-stairs room, and could see what happened. I endeavoured to form a distinction between the active and inactive people. I thought I did so; the inactive people seemed to form a circle. I observed a person better dressed than the rest among those within the circle, who did not meddle, but seemed to be exciting and encouraging others. I saw several genteel looking men, and amongst them a black; there was one genteel man in particular, whose conduct I confess excited my indignation, and I took particular notice of him. I went down amongst the mob; I spoke to him; I made myself master of his voice; I believe if I was out of his sight I could swear to his voice; I have never seen that man since. When I first saw the black I turned to a lady and said, this is a motley crew, and of every colour. Mr. Akerman's house had then catched fire; the house in which I was was in extreme danger; my self with some others went down to desire the mob to prevent the houses of innocent people catching fire; and the mob were as active in saving those as in destroying Mr. Akerman's. I had no opportunity of making any remarks till I went to my station again, then I believe it was near nine o'clock; I heard a cry and a gingling of keys in the hands of some person; there were three or four genteel persons, but who had the keys I cannot say. Amongst them was the prisoner at the bar; he was without his hat, and his hands were down. I thought he might have his hat in his hand. The house I think was at that time destroyed; the roof was fallen in. Then those persons of the genteeler description moved off towards Smithfield, and amongst them was the prisoner.
    You had observed the black in the mob before you went down? - I had.
    Are you able to say who that black was? - No. Seeing this man afterwards I took it for granted it was him; I was certain to him the second time; he had his hat off in the middle of the mob.
    Jury. You said his hands were down, did you see any thing in his hands? - No, I did not; I took it for granted he had his hat in his hand, not having it on his head.
    Cross Examination.
    There were I believe other blacks in the mob? - I never saw but one; I saw a black at first, but did not remark him so as to swear to him.
    You could not swear to him I suppose from the difficulty every man has in his mind to swear to any black? - Yes.
    There is more difficulty to swear to a black than to a white man? - No. The second time I made my remark too judiciously to err.
    When was it you first saw the black? - After the goods were first set on fire, which was about a quarter after seven o'clock.
    What dress had the black on? - Something of a dark colour, but my remark was on his face.
    What w as remarkable in that man's face more than another black? - The make of his hair was one thing; the curls were out if he had had any; and his hair smooth on his head. His face was so exposed to my view the second time, that I could not be better situated to make any remark on his face.
     See originalHis hair was the thing by which you knew him? - His hair and his face.
    What was particular in his face? - I cannot distinguish it any other than from the weight of the impression it made on me.
    Counsel for the Crown. Have you any doubt about him? - No.
                        ANN                   WOOD                                                                                        sworn.
    I live at Mr. Jennings's, opposite Mr. Akerman's house.
    Was you at home on the Tuesday evening when Mr. Akerman's house was attacked? - I was.
    Did you in the course of that evening see the prisoner? - I did. It was a little after seven o'clock; I saw him in Mr. Akerman's two-pair-of-stairs room, he stood against the window with something in his hand and looked at me for some time before I observed particularly what he was doing. I looked at him then, and he took up something off the ground and held it up to me; when he held it up, I went down from the window into the dining-room; I came up again, and he was there still. He seemed to be looking in a drawer upon the floor, and seemed to be doing some thing up into a bundle.
    You was in the two-pair-of-stairs room opposite him? - No, I was in the three-pair-of-stairs room.
    Did you afterwards see him do any thing else? - He got up and looked at me and nodded his head at me; then I went down stairs.
    You saw him again in the course of the evening? - Yes, I saw him an hour or two afterwards in the mob.
    From the observation you made of his person are you sure that is the man? - That is the man.
    Have you any doubt about it? - No, none at all.
    Cross Examination.
    What makes you so positive that this is the man? - I know his face perfectly again by his standing and looking at me so long.
    You recollect him only by his face? - His face and his hair.
    Did you see any other black there? - Yes, I did; not in the house but in the mob.
    Could you swear to him? - I do not know that I could. I took more notice of this man than I did of any other.
    Court. What were the other people doing when the prisoner was in the two-pair-of-stairs room? - Some of the mob were pulling the house down, and some were running in with the fire to set the parlour on fire.
    Jury. How many times did you see this prisoner? - Two or three times.
    Had he his hat on when you saw him? - Yes.
                        ANN                   LESSAR                                                                                        sworn.
    Do you know the prisoner? - Yes.
    Where do you live? - I lodge in the same lodging, in which the prisoner lodged; I took the lodging of him and the landlady.
    Do you remember his coming to you and bringing you any stockings? - He gave me three pair of stockings to mark.
    What mark did he bid you put upon them? - Any kind of mark to distinguish them at the washerwoman's. I put BB, the initials of his name upon them.
    Had he left a trunk in the room? - Yes, the trunk was found there by the constable when he came; it was locked, he had the key of it.
    Who had the key of the room? - I had; nobody could get at the box without my knowledge.
                        PERCIVAL                   PHILLIPS                                                                                        sworn.
    I am a constable. I searched the lodging of the prisoner last Tuesday-week.
    Did you find a trunk there? - I did.
    Did you find any thing in that trunk? - Yes; these stockings, this pocket book, and a handkerchief. (producing them.)
    Any thing else? - This key (producing it) was upon the shelf in the lodging.
    Mr.                                   RICHARD                   AKERMAN                                                                                        sworn.
    This pocket-book, I believe, has been in my possession thirty years; it was, I believe, in one of the drawers belonging to my wife; here are several of my banker's cheques which had my name to them.
    Look at the stockings? - Here is a very remarkable pair which I had made for me, and the maker wove the initials of mySee original name in them in open work; the prisoner has put the initials of his name (B B) over it; they were in the drawers in a one-pair of stairs room. Here are several others that were marked by my sister, they are mine; I believe the handkerchiefs to be mine, but there are no particular marks on them; there are a pair of stockings that were taken off the prisoner's legs, which has the name cut out.
    To Phillips. Did you take them off the prisoner's legs? - I did.
    To Mr. Akerman. Is the place that is cut out the place where the name was wove? - Yes. This is a remarkable key; it is a key of the Park, it has a crown and my name at length upon it.
    To Lessar. Do you know any thing of the key that was found in the lodging? - No, it was on the shelf when he had the lodging?
    Was it there when he left the lodging? - I believe it was there; I saw it once or twice; I never knew the meaning of the key.
    Prisoner. My Lord, please to ask that woman if she did not wash the handkerchief the things were tied up in? - I washed a blue-and-white silk handkerchief, I cannot swear it was this, it was all over mud. I washed it on the Thursday, the first week that I was in the house.
    Was that after the burning of Newgate? - Yes. I was not in town till it was burnt.
    Prisoner. I leave my defence to my counsel and my witnesses.
    For the prisoner.
    Dr. SANDIMAN sworn.
    Do you know the prisoner? - Yes, I knew him five years ago, he lived with a relation of mine; he bore an exceeding good character; he used to come backwards and forwards to my house.
                        ROBERT                   GATES                                                                                        sworn.
    I am footman to Mr. Goodhousen in Golden Square.
    Do you know the prisoner? - I do; I have known him perfectly well from the second day after he came to England, which is six years ago; he lived with a person I knew in America, that person gave him an excellent character, and he has always borne a good character since I knew him.
                        GRACE                   ROBERTS                                                                                        sworn.
    The prisoner lay at our house the night that the prison was burnt.
    What time did you see him that night? - I am not positive to the hour he came in, it was from nine to eleven o'clock.
    What time did he come home? - I am not positive to the hour, it was a little after nine.
    Are you positive of that? - Yes.
    Where do you live? - At No. 3, in Berner's-street.
    He came home a little after nine? - Yes, I am certain of it; he continued there all that night till six in the morning, and was never out of the house.
    What day was that? - The 6th of June.
    What day of the week? - I am not certain.
    Are you sure it was the night the prison was burnt? - I am.
    What prison? - I am not certain what prison, I heard it mentioned in the family that the prison was burnt down.
    Cross Examination.
    Who bid you to remember the 6th of June? - I remember it by the people being taken up.
    When did you talk of its being the 6th of June? - I know he lay at our house on the 6th of June.
    Did you take notice of any other night when he lay there? - No.
    Did not he lie there on the 7th and 8th of June? - No, only that night.
    You are an acquaintance of his? - Yes.
    Is he a married man? - I cannot say.
    Did he bring any body with him? - No.
    Did he lie by himself? - Yes, I gave him a candle to light him to bed.
    Did you know he was to lie there that night? - Yes, he told my fellow servant so.
    You are a servant, are you? - Yes.
    Did your master know that this man was to lie in the house? - I cannot tell.
    Do you let such persons lie in the house without your master's knowledge? - He was an old servant, he lay in the servants hall.
    Other servants lie there? - Yes, there was a black lay there.
     See original                    JOHN                   NORTHINGTON                                                                                        (a Black) sworn.
    I am servant to Mr. Wood.
    Did the prisoner lie at your house? - Yes, on the night that Holbourn was on fire.
    When the house of Mr. Langdale was on fire? - Yes, the man that lives in Holbourn.
    Counsel for the Crown. That was on Wednesday night, the 7th?
    To Roberts. Where did the prisoner use to sleep at other times? - In the same bed.
    That was when he was a servant there? - Yes.
    When he was not a servant there where did he sleep? - He never lay at our house when he was not a servant but that night; I cannot be positive to the night nor the day of the week; I say nothing but the truth.
    Prisoner to                                   Ann                   Wood                                                                                       . What dress had I on that night? - A light brownish coat, a round hat, and a red waistcoat.
                                                          GUILTY             (                                                         Death            .)
    Tried by the Second London Jury before Mr. Justice NARES.
    View as XML
     
    Version 8.0 | March 2018
    
    © 2003-2018 Old Bailey Proceedings Online
    We welcome your feedback on this web site

