##趣皮士服务端官方api
###1、获取趣皮士支持的国家
`http://www.tripsters.cn/index.php?m=partner&c=country&a=getSupportCountry`

	Get请求
	参数：
	appid：趣皮士分配的appid。test为测试appid

例如：

	http://www.tripsters.cn/index.php?m=partner&c=country&a=getSupportCountry&appid=test
	注：
	appid=test 仅返回两条数据，通过申请正式的appid才能返回趣皮士支持的所有的数据
	json返回值：
	{
			errorcode: "0",
			data:  [
			{
				country_name_cn: "泰国",
				country_name_en: "Thailand",
				country_name_local: "ประเทศไทย",
				country_code: "th", pic: "http://www.tripsters.cn/download/country/taiguo.jpg",
				hot: "1"
			},
			{
				country_name_cn: "韩国",
				country_name_en: "Korea",
				country_name_local: "대한민국", pic: "http://www.tripsters.cn/download/country/taiguo.jpg",
				country_code: "kr",
				hot: "1"
			}
			]
	}

		errorcode：错误码
		country_name_cn：国家的中文名称
		country_name_en：国家的英文名称
		country_name_local：国家的当地语名称
		country_code：国家代码（唯一）
		hot：1：开通，2：试运营
		pic:国家题图

###2、获取支持的城市
`http://www.tripsters.cn/index.php?m=partner&c=country&a=getSupportCity`
	
	Get请求
	参数：
	appid：趣皮士分配的appid。test为测试appid
	country_code：国家代码

例如：
	
	http://www.tripsters.cn/index.php?m=partner&c=country&a=getSupportCity&appid=test&country_code=th
	注：
	appid=test 仅返回两条数据，通过申请正式的appid才能返回趣皮士支持的所有的数据
	json返回值：

	{
			errorcode: "0",
			data:  [
			 {
				id: "1",
				country_code: "th",
				city_name_cn: "曼谷",
				city_name_en: "Bangkok",
				city_name_local: "กรุงเทพฯ",
				city_hot: "1"
			},
			 {
				id: "2",
				country_code: "th",
				city_name_cn: "清迈",
				city_name_en: "Chiang Mai",
				city_name_local: "เชียงใหม่",
				city_hot: "1"
			}
			]
	}
		
		errorcode：错误码
		id:趣皮士分配的城市id
		city_name_cn：国家的中文名称
		city_name_en：国家的英文名称
		city_name_local：国家的当地语名称
		city_hot：1：该国家的热门城市，2：该国家的非热门城市


###3、发送问题

`http://www.tripsters.cn/index.php?m=partner&c=question&a=sendQuestionById`

	post请求
	参数：
	appid:应用id（必填）
	user_id:趣皮士的用户id（必填）
	title：问题的标题，限长60个字（必填）
	country：国家，中文国家名（必填）
	city：国家对应的城市，用趣皮士提供的城市id，中间为英文逗号隔开如：34,45最多为两个城市，至少为一个，最多两个（必填）
	version：版本号（必填）
	platform：android 还是ios（必填）
	pic：问题图片的流，限制为一张（可选）
	lat：问题的维度，格式为：13.7372358（可选）
	lng：问题的精度，格式为：100.5391834（可选）
	address：提问问题的地址，由经纬度解析出来（可选）

	返回：
		{
				errorcode: "0",
				data:  
				 {
				question_id: “14910”
				}
				
		}
		errorcode：错误码
		question_id:提问成功返回的id

###4、问题的回答
`http://www.tripsters.cn/index.php?m=partner&c=question&a=getAnswer`

	Get请求
	参数：
	appid：趣皮士分配的appid。test为测试appid
	question_id:趣皮士提供的问题的id
	page:第几页，从1开始
	pagesize：每页的数量，默认为20，当返回不足20条，意味着没有更多了

例如：

	http://www.tripsters.cn/index.php?m=partner&c=question&a=getAnswer&appid=test&question_id=14849&page=1&pagesize=20
	
	注：
	appid=test 仅返回问题为14849的回复，通过申请正式的appid才能返回趣皮士支持的所有的数据
	
	json返回如下：按照时间倒序
	{
				errorcode: "0",
				data:  [
				{
					answer_id: "102749",
					question_id: "14849",
					detail: "回复🇳🇱曼谷小明: 具体地址 和名字",
					created: "1453273142",
					pic: null,
					user_id: "106676",
					userinfo:  {
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					}
				},
				{
					answer_id: "102748",
					question_id: "14849",
					detail: "回复白承伟 （ชัชชัย）: 这是他们家周边",
					created: "1453273084",
					pic:  {
						id: "569f2ffc1970b",
						pic: "http://123.57.60.89/Uploads/tripsters/answer/20160120/569f2ffc1970b.jpg",
						height: 2448,
						width: 3264,
						pic_small: "http://123.57.60.89/Uploads/tripsters/answer/20160120/small569f2ffc1970b.jpg",
						small_height: 90,
						small_width: 120,
						pic_middle: "http://123.57.60.89/Uploads/tripsters/answer/20160120/middle569f2ffc1970b.jpg",
						middle_height: 270,
						middle_width: 360
					},
					user_id: "106676",
					userinfo:  {
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					}
				},
				{
					answer_id: "102735",
					question_id: "14849",
					detail: "回复酱油打了很多年: 他家周围 有人知道不",
					created: "1453272052",
					pic:  {
						id: "569f2bf493404",
						pic: "http://123.57.60.89/Uploads/tripsters/answer/20160120/569f2bf493404.jpg",
						height: 2448,
						width: 3264,
						pic_small: "http://123.57.60.89/Uploads/tripsters/answer/20160120/small569f2bf493404.jpg",
						small_height: 90,
						small_width: 120,
						pic_middle: "http://123.57.60.89/Uploads/tripsters/answer/20160120/middle569f2bf493404.jpg",
						middle_height: 270,
						middle_width: 360
					},
					user_id: "106676",
					userinfo:  {
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					}
				},				 {
					answer_id: "102733",
					question_id: "14849",
					detail: "这是他家周围 你们看看呢？",
					created: "1453271989",
					pic:  {
						id: "569f2bb52267b",
						pic: "http://123.57.60.89/Uploads/tripsters/answer/20160120/569f2bb52267b.jpg",
						height: 2448,
						width: 3264,
						pic_small: "http://123.57.60.89/Uploads/tripsters/answer/20160120/small569f2bb52267b.jpg",
						small_height: 90,
						small_width: 120,
						pic_middle: "http://123.57.60.89/Uploads/tripsters/answer/20160120/middle569f2bb52267b.jpg",
						middle_height: 270,
						middle_width: 360
					},
					user_id: "106676",
					userinfo:  {
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					}
				},				 {
					answer_id: "102596",
					question_id: "14849",
					detail: "回复🇳🇱曼谷小明: 不是 这是一家果汁店",
					created: "1453255950",
					pic: null,
					user_id: "106676",
					userinfo: 
					{
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					}
				},				 {
					answer_id: "102595",
					question_id: "14849",
					detail: "回复酱油打了很多年: 吃过了 就是想去图片这家吃吃他们家的鲜榨果汁",
					created: "1453255922",
					pic: null,
					user_id: "106676",
					userinfo:  {
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					}
				},
				{
					answer_id: "102593",
					question_id: "14849",
					detail: "回复白承伟 （ชัชชัย）: 没有 就只有这张😂",
					created: "1453255861",
					pic: null,
					user_id: "106676",
					userinfo:  {
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					}
				},				 {
					answer_id: "102498",
					question_id: "14849",
					detail: "这是在轻轨站上面的一家奶茶店吧。。。",
					created: "1453226833",
					pic: null,
					user_id: "110071",
					userinfo:  {
						id: "110071",
						open_id: "o2LGDuBCT7P2RitfofOKd-blFa9w",
						nickname: "🇳🇱曼谷小明",
						identity: "2",
						avatar: "http://123.57.60.89/Uploads/tripsters/user/20151229/568243bc03ebb.jpg",
						gender: "m",
						location: "曼谷",
						country: "泰国"
					}
				},				 {
					answer_id: "102493",
					question_id: "14849",
					detail: "是MangoTango吗？感觉又不像。。。其实mangoTango就很好喝了，这是地址 ถนน พระราม 1 Pathum Wan, Bangkok 10330泰国 可以去试试～",
					created: "1453223330",
					pic: null,
					user_id: "110447",
					userinfo:  {
						id: "110447",
						open_id: null,
						nickname: "酱油打了很多年",
						identity: "2",
						avatar: "http://123.57.60.89/Uploads/tripsters/user/20151121/565033b5ebb0e.jpg",
						gender: "m",
						location: "泰国 ",
						country: "泰国"
					}
				},				 {
					answer_id: "102491",
					question_id: "14849",
					detail: "太模糊了。",
					created: "1453223031",
					pic: null,
					user_id: "111319",
					userinfo:  {
						id: "111319",
						open_id: "o2LGDuLLY6YhUHlEPKOUP06jADxY",
						nickname: "LlWwQq657",
						identity: "2",
						avatar: "http://123.57.60.89/Uploads/tripsters/user/20151218/5673f453cccae.jpg",
						gender: "f",
						location: "广西 南宁",
						country: "泰国"
					}
				},				 {
					answer_id: "102490",
					question_id: "14849",
					detail: "这张图看不清楚呐~~",
					created: "1453222956",
					pic: null,
					user_id: "111346",
					userinfo:  {
						id: "111346",
						open_id: "5520496719",
						nickname: "肉嘟嘟中二少女",
						identity: "2",
						avatar: "http://tp4.sinaimg.cn/5520496719/180/5742873225/0",
						gender: "f",
						location: "海外 泰国",
						country: "泰国"
					}
				},				 {
					answer_id: "102489",
					question_id: "14849",
					detail: "看不清啊 有更清楚一点的图吗",
					created: "1453222932",
					pic: null,
					user_id: "101729",
					userinfo:  {
						id: "101729",
						open_id: "o2LGDuK6xwNpTvj2Hb9aLJFcJV24",
						nickname: "白承伟 （ชัชชัย）",
						identity: "2",
						avatar: "http://123.57.60.89/Uploads/tripsters/user/20160216/56c2e8e11f7ed.jpg",
						gender: "m",
						location: "泰国",
						country: "泰国"
					}
				}
				]
	}
		errorcode：错误码
		answer_id:回答id
		question_id:问题id
		detail:回复详情
		created:创建时间
		pic：图片结构
			pic：原图url
			height：原图高
			width：原告宽
			pic_small：小图url
			small_height:小图高
		        small_width:小图宽
		user_id:回复的用户id
		userinfo:回复人的用户信息结构
			id：趣皮士里的id
			open_id:用户在第三方的user_id,提问时提供的user_id
			nickname：昵称
			identity：用户身份1为游客2为达人
			avatar：用户头像
			gender：性别m：男、f：女、n：未知 
			      location:用户住址
			      country：达人所属国家，当identity为2的时候有值
###5、获取问题
`http://www.tripsters.cn/index.php?m=partner&c=question&a=getQuestion`

	Get请求
	参数：
	appid：趣皮士分配的appid。test为测试appid
	country:中文国家名，当country为''空串是，返回所有国家的混合,m默认为空串
	mode:all为趣皮士的所有问题，myself在当前appid下的所有问题,默认为all
	page:第几页，从1开始
	pagesize：每页的数量，默认为20，最大为50，当返回数量<pagesize，意味着没有更多了

	备注：
	当mode为all的时候，趣皮士最大返回200条数据，按照时间倒序
例如：

	http://www.tripsters.cn/index.php?m=partner&c=question&a=getQuestion&appid=test&country=泰国&mode=all&page=1&pagesize=20
	&mode=all&page=1&pagesize=20

	注：
	appid=test 仅返回两条数据
	json返回值
	{
			errorcode: "0",
			data: [	
				{
					question_id: "323",
					title: "曼谷到清迈火车",
					created: "1428657420",
					answer_num: "2",
					user_id: "81",
					lat: null,
					lng: null,
					address: null,
					country: {
							country_code: "th",
							country_name_cn: "泰国",
							country_name_en: "Thailand",
							country_name_local: "ประเทศไทย"
						},
					pic: null,
					userinfo: {
							id: "81",
							open_id: "5584769187",
							nickname: "Candy_Wie",
							identity: "1",
							avatar: "http://tp4.sinaimg.cn/5584769187/50/572388028",
							gender: "f",
							location: "江苏 南京",
							country: ""
						},
					city: [
						{
							id: "1",
							city_name_cn: "曼谷",
							city_name_en: "Bangkok",
							city_name_local: "กรุงเทพฯ"
						},
						{
							id: "2",
							city_name_cn: "清迈",
							city_name_en: "Chiang Mai",
							city_name_local: "เชียงใหม่"
						}
							]
				},
				{
					question_id: "324",
					title: "泰国入境需携带多少现金",
					created: "1428654540",
					answer_num: "2",
					user_id: "82",
					lat: null,
					lng: null,
					address: null,
					country: {
							country_code: "th",
							country_name_cn: "泰国",
							country_name_en: "Thailand",
							country_name_local: "ประเทศไทย"
						},
					pic: null,
					userinfo: {
							id: "82",
							open_id: "5584285804",
							nickname: "Matt_Zi",
							identity: "1",
							avatar: "http://tp1.sinaimg.cn/5584285804/50/572388013",
							gender: "m",
							location: "广西 桂林",
							country: ""
						},
					city: [
						{
							id: "1",
							city_name_cn: "曼谷",
							city_name_en: "Bangkok",
							city_name_local: "กรุงเทพฯ"
						},					 {
							id: "2",
							city_name_cn: "清迈",
							city_name_en: "Chiang Mai",
							city_name_local: "เชียงใหม่"
						}
							]
				}
			]
	}
			errorcode：错误码
			question_id：问题id
			title:问题
			created:创建时间
			answer_num:回复数量
			user_id:提问者在趣皮士中的用户id
			lat:纬度
			lng：经度
			address:地址
			country：国家结构，具体参见国家返回
			pic：图片结构
				pic：原图url
				height：原图高
				width：原告宽
				pic_small：小图url
				small_height:小图高
				small_width:小图宽
			userinfo:提问者的用户结构
				id：趣皮士里的id
				open_id:用户在第三方的user_id,提问时提供的user_id
				nickname：昵称
				identity：用户身份1为游客2为达人
				avatar：用户头像
				gender：性别m：男、f：女、n：未知 
				      location:用户住址
			      country：达人所属国家，当identity为2的时候有值
###6、获取问题详情
`http://www.tripsters.cn/index.php?m=partner&c=question&a=getQuestionDetail`

	Get请求
	参数：
	appid：趣皮士分配的appid。test为测试appid
	question_id：问题的id
例如：

	http://www.tripsters.cn/index.php?m=partner&c=question&a=getQuestionDetail&appid=test&question_id=14849
	
	注：
	appid=test 返回固定数据
	{
			errorcode: "0",
			data: 
			{
				question_id: "14849",
				title: "有谁知道这是哪家果汁店 拜托拜托好像知道 听说他们家超级好喝",
				created: "1453222720",
				answer_num: "12",
				user_id: "106676",
				lat: "13.6235161",
				lng: "100.7643006",
				address: "Thanon Wat Sriwaree Noi",
				country: 
					{
						country_code: "th",
						country_name_cn: "泰国",
						country_name_en: "Thailand",
						country_name_local: "ประเทศไทย"
					},
				pic: 
					{
						pic: "http://123.57.60.89/Uploads/tripsters/question/20160120/569e6b40324a1.jpg",
						height: "3264",
						width: "2448",
						pic_small: "http://123.57.60.89/Uploads/tripsters/question/20160120/small569e6b40324a1.jpg",
						small_height: "120",
						small_width: "90"
					},
				userinfo: 
					{
						id: "106676",
						open_id: "1927281600",
						nickname: "叶ye姗",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/1927281600/180/1297775079/0",
						gender: "f",
						location: "四川 成都",
						country: ""
					},
				city: [
						{
							id: "1",
							city_name_cn: "曼谷",
							city_name_en: "Bangkok",
							city_name_local: "กรุงเทพฯ"
						}
					]
			}
	}

		errorcode：错误码
		question_id：问题id
		title:问题
		created:创建时间
		answer_num:回复数量
		user_id:提问者在趣皮士中的用户id
		lat:纬度
		lng：经度
		address:地址
		country：国家结构，具体参见国家返回
		pic：图片结构
			pic：原图url
			height：原图高
			width：原告宽
			pic_small：小图url
			small_height:小图高
			small_width:小图宽
		userinfo:提问者的用户结构
			id：趣皮士里的id
			open_id:用户在第三方的user_id,提问时提供的user_id
			nickname：昵称
			identity：用户身份1为游客2为达人
			avatar：用户头像
			gender：性别m：男、f：女、n：未知 
			      location:用户住址
		      country：达人所属国家，当identity为2的时候有值
###7、回复问题
`http://www.tripsters.cn/index.php?m=partner&c=question&a=sendAnswerById`

	post请求
	参数：
	appid:应用id（必填）
	user_id:趣皮士用户id（必填）
	detail：回复详情，限长为255（必填）
	question_id:回复问题的id（必填）
	version：版本号（必填）
	platform：android 还是ios（必填）
	pic：问题图片的流，限制为一张（可选）



返回：

	{
		errorcode: "0",
		data:  
			{
				answer_id: “14910”
			}
				
	}
		errorcode：错误码
		answer_id:回复成功返回的id

###8、追问回复
`http://www.tripsters.cn/index.php?m=partner&c=question&a=sendReAnswerById`

	post请求
	参数：
	appid:应用id（必填）
	user_id:趣皮士的用户id（必填）
	detail：回复详情，限长为255（必填）
	question_id:回复问题的id（必填）
	answer_user_id：被追问者的用户id（趣皮士提供的user_id,不是open_id）（必填）
	version：版本号（必填）
	platform：android 还是ios（必填）
	pic：问题图片的流，限制为一张（可选）

返回：

	{
		errorcode: "0",
		data:  
			{
				answer_id: “14910”
			}
				
	}
		errorcode：错误码
		answer_id:回复成功返回的id

###9、注册用户（APP调用即可）
`http://www.tripsters.cn/index.php?m=partner&c=user&a=login`

	post请求
	参数：
	appid:应用id（必填）
	user_id:用户在自己平台的uid（必填）
	avatar：用户头像（必填）
	nickname：昵称（必填）
	gender：性别格式为：m：男、f：女、n：未知 （必填）
	location：用户的地址（可选）
	channel_id:推送的channel_id（可选）
返回：

	{
			errorcode: "0",
			data:  
				{
					id: “10468”
				}			
	}
		errorcode：错误码
		id:用户在趣皮士的id

###10、获取用户信息
`http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserInfo`

	参数：
	appid:应用id（必填）
	user_id:趣皮士的用户id

例如：

	http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserInfo&appid=test&user_id=10468

	返回：
	{
			errorcode: "0",
			data: 
			{
				id: "10468”,
				open_id: null,
				nickname: "皮皮小助手",
				gender: "f",
				avatar: "http://123.57.60.89/Uploads/tripsters/user/20150829/55e1534623155.jpg",
				identity: "2",
				location: "趣皮士总部",
				description: "趣皮士!趣你的全世界!",
				country: "官方",
				points: "50"
			}
	}
		errorcode：错误码
		id：趣皮士里的id
		open_id:用户在第三方的user_id,提问时提供的user_id
		nickname：昵称
		identity：用户身份1为游客2为达人
		avatar：用户头像
		gender：性别m：男、f：女、n：未知 
		location:用户住址
		description:个人描述
		country：达人所属国家，当identity为2的时候有值
		points：积分

###11、获取用户的提问
`http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserQuestion`

	Get请求
	参数：
	appid：趣皮士分配的appid。test为测试appid
	user_id:趣皮士分配的用户id
	page:第几页，从1开始
	pagesize：每页的数量，默认为20，最大为50，当返回数量<pagesize，意味着没有更多了

	备注：
	当用户的appid和上行的appid不匹配时，只返回改用户的最新的一条提问
	当用户的appid和上行的appid相匹配时，将分页返回该用户的所有的提问
例如：
	
	http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserQuestion&user_id=10468&appid=test&&page=1&pagesize=20

	注：
	appid=test 仅返回皮皮助手的数据
	json返回值
	{
			errorcode: "0",
			data: [
			{
				question_id: "323",
				title: "曼谷到清迈火车",
				created: "1428657420",
				answer_num: "2",
				user_id: "81",
				lat: null,
				lng: null,
				address: null,
				country: 
					{
						country_code: "th",
						country_name_cn: "泰国",
						country_name_en: "Thailand",
						country_name_local: "ประเทศไทย"
					},
				pic: null,
				userinfo: 
					{
						id: "81",
						open_id: "5584769187",
						nickname: "Candy_Wie",
						identity: "1",
						avatar: "http://tp4.sinaimg.cn/5584769187/50/572388028",
						gender: "f",
						location: "江苏 南京",
						country: ""
					},
				city: [
						{
							id: "1",
							city_name_cn: "曼谷",
							city_name_en: "Bangkok",
							city_name_local: "กรุงเทพฯ"
						},
						{
							id: "2",
							city_name_cn: "清迈",
							city_name_en: "Chiang Mai",
							city_name_local: "เชียงใหม่"
						}
						]
			},
			{
				question_id: "324",
				title: "泰国入境需携带多少现金",
				created: "1428654540",
				answer_num: "2",
				user_id: "82",
				lat: null,
				lng: null,
				address: null,
				country: 
					{
						country_code: "th",
						country_name_cn: "泰国",
						country_name_en: "Thailand",
						country_name_local: "ประเทศไทย"
					},
				pic: null,
				userinfo: 
					{
						id: "82",
						open_id: "5584285804",
						nickname: "Matt_Zi",
						identity: "1",
						avatar: "http://tp1.sinaimg.cn/5584285804/50/572388013",
						gender: "m",
						location: "广西 桂林",
						country: ""
					},
				city: [
						{
							id: "1",
							city_name_cn: "曼谷",
							city_name_en: "Bangkok",
							city_name_local: "กรุงเทพฯ"
						},			 {
							id: "2",
							city_name_cn: "清迈",
							city_name_en: "Chiang Mai",
							city_name_local: "เชียงใหม่"
						}
						]
			}
			]
	}
		errorcode：错误码
		question_id：问题id
		title:问题
		created:创建时间
		answer_num:回复数量
		user_id:提问者在趣皮士中的用户id
		lat:纬度
		lng：经度
		address:地址
		country：国家结构，具体参见国家返回
		pic：图片结构
			pic：原图url
			height：原图高
			width：原告宽
			pic_small：小图url
			small_height:小图高
			small_width:小图宽
		userinfo:提问者的用户结构
			id：趣皮士里的id
			open_id:用户在第三方的user_id,提问时提供的user_id
			nickname：昵称
			identity：用户身份1为游客2为达人
			avatar：用户头像
			gender：性别m：男、f：女、n：未知 
			      location:用户住址
		      country：达人所属国家，当identity为2的时候有值
###12、获取用户的回答
`http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserAnswer`
	
	Get请求
	参数：
	appid：趣皮士分配的appid。test为测试appid
	user_id:趣皮士分配的用户id
	page:第几页，从1开始
	pagesize：每页的数量，默认为20，最大为50，当返回数量<pagesize，意味着没有更多了
	
	备注：
	当用户的appid和上行的appid不匹配时，只返回改用户的最新的一条回复
	当用户的appid和上行的appid相匹配时，将分页返回该用户的所有的回复
例如：

	http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserAnswer&user_id=10468&appid=test&&page=1&pagesize=20
	注：
	appid=test 仅返回皮皮助手的数据
	json返回值
	{
			errorcode: "0",
			data: [	
			{
				answer_id: "127111",
				question_id: "19180",
				detail: "亲~ 稍等片刻哦，我们的翻译达人以及导游达人很快就会来联系您的。",
				created: "1456140007",
				pic: null,
				user_id: "10468",
				userinfo: 
					{
						id: "10468",
						open_id: null,
						nickname: "皮皮小助手",
						identity: "2",
						avatar: "http://123.57.60.89/Uploads/tripsters/user/20150829/55e1534623155.jpg",
						gender: "f",
						location: "趣皮士总部",
						country: "官方"
					},
				question: 
					{
						question_id: "19180",
						title: "在哪可以请到靠谱的地陪翻译导游",
						created: "1456139425",
						answer_num: "4",
						user_id: "122770",
						lat: null,
						lng: null,
						address: null,
						country: 
							{
								country_code: "th",
								country_name_cn: "泰国",
								country_name_en: "Thailand",
								country_name_local: "ประเทศไทย"
							},
						pic: null,
						city: 
							[
								{
									id: "2",
									city_name_cn: "清迈",
									city_name_en: "Chiang Mai",
									city_name_local: "เชียงใหม่"
								},			 {
									id: "4",
									city_name_cn: "芭提雅",
									city_name_en: "Pattaya",
									city_name_local: "พัทยา"
								}
							],
						userinfo: 
							{
								id: "122770",
								open_id: "o2Jfbsx906tlG5QkZxoNXkIFzatw",
								nickname: "🌂si💍si💋",
								identity: "1",
								avatar: "http://wx.qlogo.cn/mmopen/ChCs6YSVOGVEsb92UgDIMMGk78G6ibgIOZkqsvaGq8GHSE9AIniaJuYL9zDpehLwayIYib1p3z1FzOo88O9pGhiaSQ/0",
								gender: "f",
								location: "湖北 武汉",
								country: ""
							}
					}
			}
			]
	}

		errorcode:错误码
		answer_id:回答id
		question_id:问题id
		detail:回复详情
		created:创建时间
		pic：图片结构
			pic：原图url
			height：原图高
			width：原告宽
			pic_small：小图url
			small_height:小图高
		        small_width:小图宽
		user_id:回复的用户id
		userinfo:回复人的用户信息结构
			id：趣皮士里的id
			open_id:用户在第三方的user_id,提问时提供的user_id
			nickname：昵称
			identity：用户身份1为游客2为达人
			avatar：用户头像
			gender：性别m：男、f：女、n：未知 
			      location:用户住址
		      country：达人所属国家，当identity为2的时候有值
		question：问题对应的提问的结构
		question_id：问题id
		title:问题
		created:创建时间
		answer_num:回复数量
		user_id:提问者在趣皮士中的用户id
		lat:纬度
		lng：经度
		address:地址
		country：国家结构，具体参见国家返回
		pic：图片结构
			pic：原图url
			height：原图高
			width：原告宽
			pic_small：小图url
			small_height:小图高
			small_width:小图宽
		userinfo:提问者的用户结构
			id：趣皮士里的id
			open_id:用户在第三方的user_id,提问时提供的user_id
			nickname：昵称
			identity：用户身份1为游客2为达人
			avatar：用户头像
			gender：性别m：男、f：女、n：未知 
			      location:用户住址
		      country：达人所属国家，当identity为2的时候有值

###13、更新用户信息
`http://www.tripsters.cn/index.php?m=partner&c=user&a=updateUserInfo`

		参数：
		appid：趣皮士分配的appid。test为测试appid
		user_id:趣皮士分配的用户id
		channel_id:push的channel_id
返回：
		
	{
		errorcode: "0",
		data:  
			{
				id: “10468”
			}
	}
		errorcode：错误码
		id:用户在趣皮士的id
		19、获取用户收到的回复
		http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserAnswered
		Get请求
		参数：
		appid：趣皮士分配的appid。test为测试appid
		user_id:趣皮士分配的用户id
		page:第几页，从1开始
		pagesize：每页的数量，默认为20，最大为50，当返回数量<pagesize，意味着没有更多了
		
		备注：
		当用户的appid和上行的appid不匹配时，只返回改用户的最新的一条回复
		当用户的appid和上行的appid相匹配时，将分页返回该用户的所有的回复
例如：

	http://www.tripsters.cn/index.php?m=partner&c=user&a=getUserAnswered&user_id=10468&appid=test&&page=1&pagesize=20
	注：
	appid=test 仅返回皮皮助手的数据
	json返回值
	{
			errorcode: "0",
			data:[
			{
				answer_id: "127111",
				question_id: "19180",
				detail: "亲~ 稍等片刻哦，我们的翻译达人以及导游达人很快就会来联系您的。",
				created: "1456140007",
				pic: null,
				user_id: "10468",
				userinfo:
					{
						id: "10468",
						open_id: null,
						nickname: "皮皮小助手",
						identity: "2",
						avatar: "http://123.57.60.89/Uploads/tripsters/user/20150829/55e1534623155.jpg",
						gender: "f",
						location: "趣皮士总部",
						country: "官方"
					},
				question: 
					{
						question_id: "19180",
						title: "在哪可以请到靠谱的地陪翻译导游",
						created: "1456139425",
						answer_num: "4",
						user_id: "122770",
						lat: null,
						lng: null,
						address: null,
						country: 
							{
								country_code: "th",
								country_name_cn: "泰国",
								country_name_en: "Thailand",
								country_name_local: "ประเทศไทย"
							},
						pic: null,
						city: 
							[
								{
									id: "2",
									city_name_cn: "清迈",
									city_name_en: "Chiang Mai",
									city_name_local: "เชียงใหม่"
								},	
								{
									id: "4",
									city_name_cn: "芭提雅",
									city_name_en: "Pattaya",
									city_name_local: "พัทยา"
								}
							],
						userinfo:
							{
								id: "122770",
								open_id: "o2Jfbsx906tlG5QkZxoNXkIFzatw",
								nickname: "🌂si💍si💋",
								identity: "1",
								avatar: "http://wx.qlogo.cn/mmopen/ChCs6YSVOGVEsb92UgDIMMGk78G6ibgIOZkqsvaGq8GHSE9AIniaJuYL9zDpehLwayIYib1p3z1FzOo88O9pGhiaSQ/0",
								gender: "f",
								location: "湖北 武汉",
								country: ""
							}
					}
			}
			]
	}

		errorcode:错误码
		answer_id:回答id
		question_id:问题id
		detail:回复详情
		created:创建时间
		pic：图片结构
			pic：原图url
			height：原图高
			width：原告宽
			pic_small：小图url
			small_height:小图高
		        small_width:小图宽
		user_id:回复的用户id
		userinfo:回复人的用户信息结构
			id：趣皮士里的id
			open_id:用户在第三方的user_id,提问时提供的user_id
			nickname：昵称
			identity：用户身份1为游客2为达人
			avatar：用户头像
			gender：性别m：男、f：女、n：未知 
			      location:用户住址
		      country：达人所属国家，当identity为2的时候有值
		question：问题对应的提问的结构
		question_id：问题id
		title:问题
		created:创建时间
		answer_num:回复数量
		user_id:提问者在趣皮士中的用户id
		lat:纬度
		lng：经度
		address:地址
		country：国家结构，具体参见国家返回
		pic：图片结构
			pic：原图url
			height：原图高
			width：原告宽
			pic_small：小图url
			small_height:小图高
			small_width:小图宽
		userinfo:提问者的用户结构
			id：趣皮士里的id
			open_id:用户在第三方的user_id,提问时提供的user_id
			nickname：昵称
			identity：用户身份1为游客2为达人
			avatar：用户头像
			gender：性别m：男、f：女、n：未知 
			      location:用户住址
		      country：达人所属国家，当identity为2的时候有值


##二、错误码
	errorcode:

	0:正常

	10001：
	appid为空
	errmsg:appid is emptey

	10002：
	错误的appid
	errmsg:invalid appid

	10003：
	接收回复的url为空
	errmsg:url is null

	10004：
	接收追问的url为空
	errmsg:url is null	
	
	20001：
	数据为空
	errmsg:data is empty	
	
	30001:
	用户信息不完整，用户user_id，avatar，nickname，gender可能为空
	errmsg:User information is not complete

	30002:
	性别信息不完整，性别不是m，f，n中的一个值
	errmsg:Gender information is not complete

	30003:
	用户被拉黑
	errmsg:This user has been added to the blacklist

	30004:
	用户注册失败
	errmsg:register error

	30005:
	用户不存在
	errmsg:user does not exist

	30006:
	更新用户信息失败
	errmsg:update error
		
	40001:
	提问信息不完整
	errmsg：Question information is not complete

	40002:
	提问问题数超过最大数
	errmsg：Data exceed the maximum value

	40003:
	追问信息不完整
	errmsg：Reanswer information is not complete

	40004:
	回复的问题不存在
	errmsg：Reply to the problem does not exist

	40005:
	回复的人不存在
	errmsg:Reply to the User does not exist

	40006:
	城市的数据格式不对
	errmsg:city is not numeric

	40007:
	提交的城市数量不对，城市至少一个，不超过2个
	errmsg:The number of abnormal City array

