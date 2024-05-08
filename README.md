# CardGame
A card game using QT, C++, show hand

code price: 600
WX: help-assignment

COMP282 The C++ Programming Language
University of Liverpool Department of Computer Science
Assignment CA2 : C++ GUI Application (Card Game)

3. Overview
Create a basic GUI card game using C++ with Qt and organise the game structure using OOP
methods.
Royalty-free card images will be available for you to download from the COMP282 Canvas page for
you to use in the application if you choose. These will consist of 52 PNG images of standard playing
cards.
If you are not familiar with the standard 52 card deck of playing cards, Wikipedia goes into lots of
detail here: https://en.wikipedia.org/wiki/Standard_52-card_deck which you may find informative.
Our game is based loosely on the hands of the classic card game, Poker. We will define the rules of
the game as follows:

1. Objective: The objective of the game is to beat a computer opponent with combinations of 5 cards (known as a Hand) worth the highest value.
2. Card Value:
a. Cards have a value of 1 to 14 and a suit chosen from Hearts (♥), Diamonds (♦), Spades (♠) and Clubs (♣). There are 52 cards in a Deck consisting of 13 cards in each suit. There are no other cards (such as Jokers) needed in the game, and only one deck is used.
b. Value ranges from 1 (low Ace) through the numbered cards worth 2 – 10 then 11 (Jack), 12 (Queen), 13 (King) and 14 (high Ace). Note that the Ace can be chosen to be worth 1 or 14 as desired to match with other held cards, this is useful for straight hands.
c. The value of cards is used to determine the winner when hands have the same rank (more on ranks and categories later), e.g. both players have One Pair. If the value of the rank cards are the same, the values of the remaining cards are used, e.g.: Player has a pair of 10s, Computer has a pair of 7s, so Player wins. Player has a hand of |10♠|10♥|2♣|3♣|5♦| and Computer has a hand of |10♦|10♠|9♣|6♥|4♠| In this case both players have One Pair of the same value (10). So we determine the value of the remaining cards, which are 10 for Player (2+3+5) and 19 for Computer (9+6+4), so Computer wins.
d. The suit is only used when determining a Flush (all cards the same suit).
e. No suit has a higher value than another. E.g. a Flush of hearts and a flush of clubs with the same numerical cards are worth the same.
3. The rank and name of the combinations are as follows, with the highest values being statistically less likely to occur and which automatically beats any card combination from a lower category. E.g. any Straight Flush beats any Four-of-a-Kind:
4. If both players have a Straight Flush the one with the highest card wins, otherwise it is a draw.
5. If both players have Four-of-a-Kind the higher card wins, e.g. four 8s would beat four 5s. It is not possible for both players to have the same 4 cards so the winner can always be found by comparing these.
6. If both players have Full House the higher card of the group of three wins, e.g. three 4s and two Queens would beat three 2s and two kings. It is not possible for both players to have three cards of the same value so the winner can always be found by comparing these.
7. If both players have a Flush the highest card wins, in this example a Jack. If both players have a flush and the same highest cards the next highest are compared, e.g. K, 10, 8, 7, 5 would beat K, 10, 8, 7, 3. If the cards are still same the same, e.g. both players have 10, 8, 5, 4 and 2 in different suits it’s a draw.
8. Examples of Straights are A-5, 2-6, 3-7, 4-8, 5-9, 6-10 (as example), 7-J, 8-Q, 9-K, 10-A. Note that the Ace can be worth both 1 or 14 giving two possible straights that include it, e.g. (A, 2, 3, 4, 5) or (10, J, Q, K, A). In all other situations the Ace is always worth 14. If both players get a Straight the highest card of each wins, e.g. 9-Q would beat 3-7. If the high card of both straight is the same, it’s a draw.
9. If both players have Three-of-a-Kind the higher card wins, e.g. three Jacks would beat three 8s. It is not possible for both players to have three cards of the same value so the winner can always be found by comparing these.
10. If both players have Two Pair the highest pair wins, e.g. a pair of queens and a pair of 3s beats a pair of 10s and a pair of 9s. If both pairs are the same for each player the highest fifth card determines the winner, e.g. J, J, 8, 8, A beats J, J, 8, 8, 10 with deciding Ace being worth 14 not 1. A draw is possible.
11. If both players have One Pair the highest pair wins, e.g. a pair of 7s beats a pair of 2s. If the pair is the same for each player the highest of the remaining three cards determines the winner. A draw is possible.
12. The High Card result is determined by the highest card and continues until the last card. E.g. Q, 8, 5, 4, 3 beats Q, 8, 5, 4, 2. A draw is possible.
5. Basic Gameplay (45 marks)
1. There should be a ‘start’ (or ‘deal’) button on the game window. When this button is clicked, the game starts.
2. The cards are shuffled before each game.
3. For each Round, 10 cards taken from the shuffled Deck and distributed to the Player and the Computer, making two hands with 5 cards each.
4. When a card has been used in a hand, it cannot be used again during that game (but bear in mind the ‘advanced gameplay’ sections below).
5. Each game consists of rounds. When a new round is started but there are less than 10 cards left in the deck, the game ends (since we cannot deal full hands to the players).
6. At the start of each round, the game window should display a representation of the player’s hand (5 cards) and the computer’s hand (5 cards). This can be text-based, but you will get marks for using images. Under each card, it should say the name of the card (e.g. ‘6 of Spades’ or ‘6♠’).
7. The game should work out the categories (and therefore the rank) of each of the hands. Above the cards, there should be a label that displays the category of the hand (e.g. ‘Full House’).
8. Based on those ranks, the game should determine who has the strongest hand. This should also be displayed.
9. There should be a button marked ‘Next Round’ which will move the game on to the next round. If there are no more rounds, the button should be marked ‘Finish Game’.
10. A score should be displayed and updated at the start of each round, that shows the player’s score and the computer’s score. The scores represent the number of hands won in the game.
11. After the 5 rounds have been played, the winner should be announced (or a draw declared if applicable), and the player should be able to play another game if they wish to.
6. Advanced gameplay (10 marks)
In rounds 1-4, allow the player to swap up to three cards from their hand with cards from the deck. It’s up to you how to implement the interface for this (perhaps ‘Swap’ buttons, or perhaps by clicking the card, or another method of your choosing). Don’t allow swapping in Round 5 (because in Round 5
there will be only 2 cards left in the deck). The cards that are swapped out of the player’s hand can still remain in the game (i.e. they are replaced in the Deck at a random location).

7. Even more advanced gameplay (10 marks)
If the player swaps a card, the computer has the opportunity to swap a card from its deck too. The computer will have to determine whether or not it is advantageous to swap a card (if the computer has a Straight Flush hand, it won’t be worth swapping, for example, but if it has 1 pair it may want to
swap one of the other cards to attempt to improve the hand). This can be as basic or complex as you like. A basic version may just scan a hand for groups of two, three or four cards of the same value and swap any remaining cards to try to improve this. A more advanced system may calculate the probabilities of getting a straight or flush hand.

8. Suggested Classes/Objects and Methods in the game
You are free to code the game as you like. But please ensure that you have classes called: Game, Player, Card, Deck, Hand.
There are some suggested structures and methods below which you may find helpful.
Game class: Consists of two Players. Once the game has been completed the winner (or a draw) is declared. Game state is shown in a game window as text and/or graphics of cards held with buttons for triggering methods.
Player class: A class representing a player with a name and a score of hands won. Each Player has a Hand of five Cards. Assume that both players can see each other’s cards and the result is based purely on getting a strong hand of cards.
Card class: Has a value and a suit (e.g. 7 of Hearts).
Methods:
Card::getValue() returns the value as an integer, (e.g. 7). Aces are always worth 14 except when used as start of a straight.
Card::getSuit() returns the suit name as a QString, e.g. “Clubs”, “Diamonds”, “Hearts” or “Spades”.
Card::getName() returns the card name as a QString, e.g. “Jack of Clubs”, “Two of Hearts”.
Card::getNumber() returns the card type as an integer (see the section on Hand::setHand method to see how the system works). E.g. 9 of Diamonds would return 209.
Deck class: Consists of a complete standard pack of 52 cards with one of each value 2-10 and Jack,
Queen, King and Ace in each suit (4 * 13 cards).
Methods:
Deck::createDeck() generates a complete pack correctly as stated above in any order. Each card is a Card object.
Deck::shuffle() randomly puts the cards in a random order, e.g. before a game begins or after the last card is dealt.
Deck::dealCard() returns the first card in deck and continues until the entire deck has been dealt. When the last card has been dealt the entire deck is automatically shuffled so dealing can continue indefinitely.
Hand class: Holds five cards for a player, with methods to replace and order cards within it. Each player has one opportunity per round of the game (in rounds 1-4) to swap up to three cards to improve their hand. After this, the winner (or a draw) is determined.
Hand::dealHand(Deck& deck): Creates a new hand of five cards from a deck, replacing any existing cards in the hand.
Hand::sortValue(): Sorts cards in value order from smallest to largest.
E.g., a hand with cards 8, Q, 2, A, 2 would be sorted to 2, 2, 8, Q, A, considering A as 14 when not part of a straight.
Hand::sortGroup() : sorts the cards in a hand based on the frequency of each card’s value, placing the most frequent values first. For example, a hand containing the cards 2, 7, 7, 2, 7 would be rearranged to 7, 7, 7, 2, 2, grouping all 7s together followed by the 2s due to the higher frequency of
7s. If there are groups of equal size, such as two pairs or two triples, the groups are ordered by the card value in ascending order. For instance, a hand with cards 6, King, 8, 6, King (where King represents a higher value, typically 13) would be sorted to 6, 6, King, King, 8. This is because both pairs (6s and Kings) have the same frequency, and 6 is numerically smaller than King. In cases where no multiples are present, meaning all cards have unique values, the method defaults to sorting by individual card values in ascending order. This functionality is achieved by calling the sortValue() method, which organises cards from lowest to highest value.
Hand::getBest(): Calculates the highest value in the hand as shown above and returns, from highest to lowest value, a four-character QString: “stfl”, “four”, “full”, “flsh”, “strt”, “trio”, “twop”, “pair”, “high”.
Hand::setHand(const QVector& cardValues):
Sets a hand to specific cards defined in a five-element integer QVector.
The first digit (s) of each integer is the suit in alphabetical order:
1 = club, 2 = diamond, 3 = heart, 4 = spade.
The next two digits (vv) are the value of the card:
01 = Ace, 02-10 = number card, 11 = Jack, 12 = Queen, 13 = King.
These values define Card objects representing the correct card which then replaces the existing hand.
Example:
Hand::setHand({111, 311, 411, 201, 308})
defines the hand: Jack of Clubs, Jack of Hearts, Jack of Spades, Ace of Diamonds, Eight of Hearts.
For Advanced Gameplay tasks:
Hand::swapCard(const QVector& cardIndices, Deck& deck): Replaces up to
three specified cards with the next card in the deck.
Examples:
myHand.swapCard({1, 3}, myDeck);
replaces the first and third cards in deck ‘myDeck’.
myHand.swapCard({3, 4, 5}, myDeck);
replaces the third, fourth, and fifth cards in deck ‘myDeck’.
myHand.swapCard({1, 3, 1}, myDeck);
replaces the first and third cards and ignores the duplication of the first card.
myHand.swapCard({1, 3, 4, 5}, myDeck);
replaces cards 1, 3, and 4; the fourth value is ignored.
myHand.swapCard({}, myDeck);
does nothing.
Order does not matter, e.g., myHand.swapCard({3, 4, 5}, myDeck);
is the same as myHand.swapCard({5, 3, 4}, myDeck);
WX: help-assignment

扑克游戏（梭哈，show hand）
1.游戏窗口上应该有一个＂开始”（或＂发牌＂）按钮。点击该按钮后，游戏就开始了。
2.每局游戏前都要洗牌。
3.每轮从洗好的牌堆中抽出10张牌，分发给玩家和电脑，两手各有5张牌。
4.当一张牌在手牌中使用过之后，在该局游戏中就不能再使用了（但请记住下面的＂高级玩法“部分）。
5．每局游戏由几轮组成。当新一轮游戏开始，但牌组中剩下的牌少于10张时，游戏结束（因为我们不能给玩家发满手牌）。
6．每轮游戏开始时，游戏窗口应显示玩家的手牌（5张）和电脑的手牌（5张）。这可以是文字，但使用图片会得到分数。每张牌下面都应写明牌名（例如“黑桃6＂或°(9
7．游戏应计算出每一手牌的类别（以及等级）。牌的上方应有一个标签，显示牌的类别（如“葫芦”）。
8．游戏应根据这些等级来决定谁的牌最强。这也应该显示出来。
9．应该有一个标有“下一轮”的按钮，该按钮会将游戏推进到下一轮。如果没有下一轮了，按钮上应该标有“结束游戏”。
10．每轮游戏开始时都应显示和更新分数，显示玩家的分数和计算机的分数。分数代表游戏中获胜的手数。
11.5轮比赛结束后，应宣布获胜者（或宣布平局（如适用）），如果选手愿意，还可以再玩一局。
在第1—4轮中，允许玩家用牌组中的牌交换最多三张手牌。如何实现这一功能取决于您的界面（也许是“交换＂按钮，也许是点击卡牌，或者您选择的其他方法）。第5轮不允许换牌（因为第5轮时牌组将只剩下2张牌）。从玩家手中换出的卡牌仍可留在游戏中（即它们会被随机替换到卡组中的某个位置）。
如果玩家换了一张牌，电脑也有机会从自己的牌组中换一张牌。计算机必须确定换牌是否有利（例如，如果计算机有一手同花顺，就不值得换牌，但如果计算机有一对，则可能想换其他牌来改善手牌）。
这可以是基本的，也可以是复杂的。基本版本可能只是扫描一手牌，找出两张、三张或四张相同价值的牌，然后交换剩下的牌，试图改善这种情况。更高级的系统可以计算出获得顺子或同花的概率。

联系方式wechat: help-assignment
代码现成，代码价格，：code price: 600
可定制化改结构以防查重。
