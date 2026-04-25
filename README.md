const ComponentFunction = function() {
  // @section:imports @depends:[]
  const React = require('react');
  const { useState, useEffect, useCallback, useMemo, useContext } = React;
  const { View, Text, StyleSheet, ScrollView, TouchableOpacity, Platform, StatusBar, Dimensions, Image, Animated } = require('react-native');
  const { MaterialIcons } = require('@expo/vector-icons');
  const { createStackNavigator } = require('@react-navigation/stack');
  const { useSafeAreaInsets } = require('react-native-safe-area-context');
  // @end:imports

  // @section:theme @depends:[]
  const primaryColor = '#8B5CF6';
  const accentColor = '#A78BFA';
  const backgroundColor = '#0D0D1A';
  const cardColor = '#1A1A2E';
  const cardColor2 = '#16213E';
  const textPrimary = '#F3F0FF';
  const textSecondary = '#A89BC2';
  const borderColor = '#2D2D4E';
  const SCREEN_WIDTH = Dimensions.get('window').width;
  const SCREEN_HEIGHT = Dimensions.get('window').height;
  // @end:theme

  // @section:navigation-setup @depends:[]
  var Stack = createStackNavigator();
  // @end:navigation-setup

  // @section:ThemeContext @depends:[theme]
  const ThemeContext = React.createContext({
    theme: {
      colors: {
        primary: primaryColor,
        accent: accentColor,
        background: backgroundColor,
        card: cardColor,
        textPrimary: textPrimary,
        textSecondary: textSecondary,
        border: borderColor,
        success: '#10B981',
        error: '#EF4444',
        warning: '#F59E0B'
      }
    }
  });
  const ThemeProvider = function(props) {
    const theme = useMemo(function() {
      return {
        colors: {
          primary: primaryColor,
          accent: accentColor,
          background: backgroundColor,
          card: cardColor,
          textPrimary: textPrimary,
          textSecondary: textSecondary,
          border: borderColor,
          success: '#10B981',
          error: '#EF4444',
          warning: '#F59E0B'
        }
      };
    }, []);
    const value = useMemo(function() { return { theme: theme }; }, [theme]);
    return React.createElement(ThemeContext.Provider, { value: value }, props.children);
  };
  const useTheme = function() { return useContext(ThemeContext); };
  // @end:ThemeContext

  // @section:chapters-data @depends:[]
  var CHAPTERS = [
    {
      id: 'cousins-gang',
      title: 'Cousins Gang',
      subtitle: 'Tamim, Imtiaz, Inayat, Farhad, Ricky, Lipika, Joba, Hina, Siddika',
      emoji: '👨‍👩‍👧‍👦',
      color: '#7C3AED',
      gradientStart: '#4C1D95',
      preview: 'Nine souls, one heartbeat. This is the story of our gang...',
      story: 'We were nine cousins — Tamim, Imtiaz, Inayat, Farhad, Ricky Kokai, Lipika, Joba, Hina, and Siddika. Different in age, different in nature, but bound by something thicker than blood — a shared childhood that no one could ever take away from us.\n\nTamim was always the smart one, the quiet observer who noticed everything. Imtiaz brought the mischief — no plan was complete without his wild ideas. Inayat was the gentle soul, the one who cried at movies and pretended he didn\'t. Farhad was our protector, always the first to stand up when someone needed defending.\n\nRicky Kokai had a laugh so loud it could wake the whole neighborhood. Lipika was the fashionable one, always ahead of everyone in style. Joba was the storyteller, keeping us entertained for hours. Hina was the peacemaker, the one who always made us hug after a fight. And Siddika — the youngest but the boldest — never afraid to speak her truth.\n\nTogether, we were unstoppable. Together, we were home.\n\nThose summer vacations, those festive nights, those lazy afternoons on the rooftop — we didn\'t know then that those moments were golden. We didn\'t know that one day, life would pull us in different directions, and we\'d spend years trying to recreate what we had so easily back then.\n\nBut in our hearts, the gang lives on. Forever nine. Forever us.'
    },
    {
      id: 'ladai-bhi-pyaar-bhi',
      title: 'Ladai Bhi Pyaar Bhi',
      subtitle: 'Fights and Love, all in one breath',
      emoji: '💢❤️',
      color: '#DC2626',
      gradientStart: '#7F1D1D',
      preview: 'We fought like enemies and loved like family — sometimes both at once...',
      story: 'There is a special kind of relationship that only cousins understand — where you can have a screaming match in the afternoon and share a plate of biryani at dinner, completely forgetting why you were even angry.\n\nWe fought over everything. The TV remote was a battlefield. Whose turn it was to sleep on the good mattress was a diplomatic crisis. Who ate the last piece of cake was practically a war crime. Imtiaz and Farhad once didn\'t speak for three whole days because of a cricket match argument. Three days — and then Farhad saw Imtiaz alone in the corner looking sad, and without a word, sat next to him and handed him a biscuit.\n\nThat was us. That was always us.\n\nLipika and Joba had the most dramatic fights — full of tears and "I\'m never talking to you again!" — and were best friends again within the hour. Hina always tried to mediate, but sometimes she ended up crying too because nobody was listening.\n\nSiddika, being the youngest, had a special power: one tear and everyone would stop fighting to comfort her. She used it wisely.\n\nBut here\'s what I remember most about our fights — nobody ever stayed angry. Not really. Because at the end of the day, we all slept in the same room, under the same roof, and the warmth of family was stronger than any grudge.\n\nLadai bhi thi, pyaar bhi tha. And the pyaar always won.'
    },
    {
      id: 'roasting-moments',
      title: 'Roasting Moments',
      subtitle: 'When we laughed until our stomachs hurt',
      emoji: '🔥😂',
      color: '#D97706',
      gradientStart: '#78350F',
      preview: 'Nobody was safe from the roast sessions. Nobody. Not even the roasters...',
      story: 'In our gang, roasting was a love language.\n\nIf you weren\'t being teased, you were either invisible or too boring to deserve attention. And in our family, nobody wanted to be either.\n\nRicky Kokai was the undisputed champion of roasting. He had a gift — he could find your most embarrassing moment, your biggest insecurity, your funniest mistake, and turn it into the most hilarious story you\'ve ever heard. Even the victim would be laughing, helplessly.\n\nRemember when Tamim tried to impress everyone with his cooking and made rice that was somehow both burnt and uncooked at the same time? Ricky described it as "a culinary miracle that defied the laws of physics." Tamim cried-laughed for ten minutes.\n\nOr when Imtiaz fell asleep during the Eid prayer and started snoring? Ricky\'s imitation of that snore became legendary. Imtiaz still can\'t live it down.\n\nAnd Farhad\'s terrible dancing at Lipika\'s birthday? Ricky choreographed a full re-enactment that had everyone on the floor.\n\nBut Ricky wasn\'t immune either. When his first attempt at a moustache came in patchy and uneven, we roasted him for weeks. "Half a caterpillar," Joba called it. Even Ricky laughed until he wheezed.\n\nThose roasting sessions weren\'t mean — they were intimate. You only roast the people you\'re comfortable with, the people you love enough to laugh at. It was our way of saying: I see you. All of you. And I love you anyway.\n\nI still hear Ricky\'s laugh in my head sometimes. It starts everything else.'
    },
    {
      id: 'new-year-party',
      title: 'New Year Party',
      subtitle: 'Midnight magic with our people',
      emoji: '🎉✨',
      color: '#0891B2',
      gradientStart: '#164E63',
      preview: 'That night we stayed up until midnight, convinced the world would change...',
      story: 'New Year\'s Eve with the cousins was unlike anything else in the world.\n\nWe\'d start planning weeks in advance — who\'s bringing what food, what games we\'d play, who was in charge of the countdown. Every year, someone promised to organize properly, and every year, we ended up improvising everything at the last minute. Somehow it was always perfect.\n\nThe day would start with everyone arriving gradually, dragging in bags of snacks and good intentions. By evening, the house was full of noise, laughter, the smell of food from the kitchen, and at least two arguments about what music to play.\n\nAs midnight approached, something magical happened. The noise softened. We\'d gather — all nine of us, sometimes more when aunties and uncles joined — and we\'d stand together watching the clock.\n\nIn those last ten seconds, someone would start the countdown. Ten... nine... eight... and our voices would join, louder with each number. Three... two... one...\n\nHAPPY NEW YEAR!\n\nAnd then chaos. Hugs. Laughing. Ricky would do something embarrassing. Hina would tear up a little. The little ones would run around screaming. Someone would blow a noisemaker directly into someone else\'s ear.\n\nIn those first seconds of a new year, surrounded by everyone I loved, I always felt invincible. Like as long as we had each other, nothing could go wrong.\n\nI didn\'t know that some of those New Year nights were already our last ones together. I didn\'t know to hold on tighter.\n\nBut I held on anyway. We all did.'
    },
    {
      id: 'batawara',
      title: 'Batawara',
      subtitle: 'The parting that broke something in all of us',
      emoji: '💔🏠',
      color: '#7C3AED',
      gradientStart: '#3B0764',
      preview: 'The day everything divided. The day childhood officially ended...',
      story: 'Batawara. Partition. The dividing of what was once whole.\n\nIt didn\'t happen all at once. It never does. It happened slowly, the way the tide goes out — you don\'t notice until you look up and the water is far away.\n\nFirst came the education — some cousins went to different cities for studies. Then came jobs, marriages, responsibilities. The house that once held all of us began to feel too big in the wrong ways and too small in others. Properties were discussed. Decisions were made. And slowly, the one big roof became many separate ones.\n\nI remember the last time all nine of us were together in the same place for more than a day. I don\'t remember what we talked about. I wish I had paid more attention. I wish I had taken more photos. I wish I had said, out loud, "I love you all, and I don\'t know when we\'ll all be here again."\n\nThe batawara wasn\'t just physical. Something emotional divided too. The ease of each other — the ability to walk into the next room and find your person — that ended. Now everything requires planning, scheduling, alignment of calendars.\n\nInayat cried, quietly, when he packed his things. I saw him. I didn\'t say anything because I knew if I acknowledged it, I would cry too.\n\nSiddika, the youngest, asked why everyone was leaving. Nobody had a good answer.\n\nBatawara is a strange grief — you\'re not mourning a death. Everyone is alive and well. But something that was alive between you has changed shape. The childhood you shared is now a place you can only visit in memory.\n\nAnd in memory, we still live there. All nine of us. Together.'
    },
    {
      id: 'miss-you-yaar',
      title: 'Miss You Yaar',
      subtitle: 'For the ones who are far but never forgotten',
      emoji: '🌙💫',
      color: '#059669',
      gradientStart: '#064E3B',
      preview: 'This is the part where we admit it — we miss each other every single day...',
      story: 'Miss you yaar.\n\nThree words that carry the weight of a thousand memories. Three words that mean: I was just eating something and thought of you. I heard that song and remembered that time. I had a bad day and wished you were here. I laughed at something and wanted to share it with you. I missed you before I even realized I was missing you.\n\nWe\'re scattered now — different cities, different countries, different lives. Some of us have children of our own. Some of us have grey in our hair that wasn\'t there before. Time moves, and we move with it, whether we want to or not.\n\nBut here is what I know:\n\nWhen Tamim\'s daughter laughs, I wonder if she laughs like him. When Imtiaz posts a photo from somewhere new, I smile and feel proud, the way you\'re proud of family. When Hina calls on Eid, those ten minutes feel like coming home. When Ricky sends a voice note that\'s mostly just him laughing at his own joke, I laugh too, alone in my room, and feel less alone.\n\nMissing people doesn\'t mean you\'ve lost them. It means they live in you — in the habits they shaped, in the jokes only you understand, in the way you see the world through eyes that were partly formed by loving them.\n\nWe are grown now. We have weight. We have responsibilities. We have the complicated, beautiful, exhausting lives that were once just futures we dreamed of on rooftops.\n\nBut somewhere, under all of that, are nine children who grew up tangled together like roots — and those roots don\'t let go.\n\nSo this is for you, Tamim, Imtiaz, Inayat, Farhad, Ricky, Lipika, Joba, Hina, and Siddika.\n\nMiss you yaar. Always.\n\n— From your cousin, with everything.'
    }
  ];
  // @end:chapters-data

  // @section:HomeScreen-ChapterCard @depends:[styles,chapters-data]
  var ChapterCard = function(props) {
    var chapter = props.chapter;
    var onPress = props.onPress;
    var index = props.index;
    var scaleAnim = useMemo(function() { return new Animated.Value(1); }, []);

    var handlePressIn = useCallback(function() {
      Animated.spring(scaleAnim, { toValue: 0.97, useNativeDriver: true, speed: 50, bounciness: 4 }).start();
    }, [scaleAnim]);

    var handlePressOut = useCallback(function() {
      Animated.spring(scaleAnim, { toValue: 1, useNativeDriver: true, speed: 50, bounciness: 4 }).start();
    }, [scaleAnim]);

    return React.createElement(Animated.View, {
      style: [styles.cardWrapper, { transform: [{ scale: scaleAnim }] }],
      key: chapter.id
    },
      React.createElement(TouchableOpacity, {
        onPress: onPress,
        onPressIn: handlePressIn,
        onPressOut: handlePressOut,
        activeOpacity: 1,
        style: styles.card,
        componentId: 'chapter-card-' + chapter.id
      },
        React.createElement(View, {
          style: [styles.cardAccentBar, { backgroundColor: chapter.color }]
        }),
        React.createElement(View, { style: styles.cardContent },
          React.createElement(View, { style: styles.cardHeader },
            React.createElement(View, {
              style: [styles.emojiContainer, { backgroundColor: chapter.gradientStart }]
            },
              React.createElement(Text, { style: styles.cardEmoji }, chapter.emoji)
            ),
            React.createElement(View, { style: styles.chapterNumberBadge },
              React.createElement(Text, { style: styles.chapterNumberText }, 'Ch. ' + (index + 1))
            )
          ),
          React.createElement(Text, { style: styles.cardTitle }, chapter.title),
          React.createElement(Text, { style: styles.cardSubtitle, numberOfLines: 2 }, chapter.subtitle),
          React.createElement(View, { style: styles.cardDivider }),
          React.createElement(Text, { style: styles.cardPreview, numberOfLines: 2 }, chapter.preview),
          React.createElement(View, { style: styles.cardFooter },
            React.createElement(Text, { style: [styles.readMoreText, { color: chapter.color }] }, 'Read Story'),
            React.createElement(MaterialIcons, { name: 'arrow-forward-ios', size: 14, color: chapter.color })
          )
        )
      )
    );
  };
  // @end:HomeScreen-ChapterCard

  // @section:HomeScreen @depends:[ThemeContext,chapters-data,HomeScreen-ChapterCard,styles]
  var HomeScreen = function(props) {
    var navigation = props.navigation;
    var insets = useSafeAreaInsets();
    var scrollTopPadding = insets.top;

    var handleChapterPress = useCallback(function(chapter) {
      navigation.push('ChapterDetail', { chapterId: chapter.id });
    }, [navigation]);

    return React.createElement(View, {
      style: [styles.screenContainer],
      componentId: 'home-screen'
    },
      React.createElement(StatusBar, { barStyle: 'light-content', backgroundColor: backgroundColor }),
      React.createElement(ScrollView, {
        style: { flex: 1 },
        contentContainerStyle: { paddingTop: scrollTopPadding, paddingBottom: insets.bottom + 24 },
        showsVerticalScrollIndicator: false
      },
        React.createElement(View, { style: styles.heroSection },
          React.createElement(View, { style: styles.heroTopRow },
            React.createElement(Text, { style: styles.heroLabel }, 'MEMORY BOOK'),
            React.createElement(View, { style: styles.heroDot })
          ),
          React.createElement(Text, { style: styles.heroTitle }, 'Cousins\nMemories'),
          React.createElement(Text, { style: styles.heroSubtitle }, 'A personal keepsake of nine cousins, one childhood, and a love that time cannot erase.'),
          React.createElement(View, { style: styles.heroImageRow },
            React.createElement(Image, {
              source: { uri: 'IMAGE:family-childhood-nostalgia-warm' },
              style: styles.heroImage,
              componentId: 'hero-image'
            }),
            React.createElement(View, { style: styles.heroImageOverlay }),
            React.createElement(View, { style: styles.heroBadge },
              React.createElement(Text, { style: styles.heroBadgeText }, '6 Chapters')
            )
          ),
          React.createElement(View, { style: styles.heroStatsRow },
            React.createElement(View, { style: styles.heroStat },
              React.createElement(Text, { style: styles.heroStatNumber }, '9'),
              React.createElement(Text, { style: styles.heroStatLabel }, 'Cousins')
            ),
            React.createElement(View, { style: styles.heroStatDivider }),
            React.createElement(View, { style: styles.heroStat },
              React.createElement(Text, { style: styles.heroStatNumber }, '∞'),
              React.createElement(Text, { style: styles.heroStatLabel }, 'Memories')
            ),
            React.createElement(View, { style: styles.heroStatDivider }),
            React.createElement(View, { style: styles.heroStat },
              React.createElement(Text, { style: styles.heroStatNumber }, '1'),
              React.createElement(Text, { style: styles.heroStatLabel }, 'Family')
            )
          )
        ),
        React.createElement(View, { style: styles.sectionHeader },
          React.createElement(Text, { style: styles.sectionTitle }, 'Chapters'),
          React.createElement(Text, { style: styles.sectionCount }, CHAPTERS.length + ' stories')
        ),
        CHAPTERS.map(function(chapter, index) {
          return React.createElement(ChapterCard, {
            key: chapter.id,
            chapter: chapter,
            index: index,
            onPress: function() { handleChapterPress(chapter); }
          });
        }),
        React.createElement(View, { style: styles.footerQuote },
          React.createElement(Text, { style: styles.footerQuoteText }, '"In the book of life, the chapters we remember most are the ones we lived together."'),
          React.createElement(Text, { style: styles.footerQuoteAuthor }, '— Cousins, always')
        )
      )
    );
  };
  // @end:HomeScreen

  // @section:ChapterDetailScreen @depends:[ThemeContext,chapters-data,styles]
  var ChapterDetailScreen = function(props) {
    var navigation = props.navigation;
    var route = props.route;
    var chapterId = route && route.params ? route.params.chapterId : null;
    var insets = useSafeAreaInsets();

    var chapter = useMemo(function() {
      if (!chapterId) return CHAPTERS[0];
      var found = null;
      for (var i = 0; i < CHAPTERS.length; i++) {
        if (CHAPTERS[i].id === chapterId) { found = CHAPTERS[i]; break; }
      }
     
