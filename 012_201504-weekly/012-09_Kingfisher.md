![이미지](../img/012-09.png)

[carthage]: https://github.com/Carthage/Carthage/
[cocoadocs]: http://cocoadocs.org/docsets/Kingfisher

 환경 : IOS8.0 이상, Xcode 6.3

 솔직히 Objective-C에 대해서는 지식이 거의 없다. 그래서 해당 ReadME의 내용을 바탕으로 실행을 해본 Review에 대해서 주로 작성 하도록 하겠습니다.

 이 프로젝트는 CocoaPods와 Carthage를 사용한다고 한다. Xcode Project의 Dependency manager가 Cocoapods라고 하며, 설치하는 프로그램이 Carthage라고 합니다. 이정도는 아시는 분도 있으시겠지만...저는 말씀드린대로 과수원(APPLE)을 재대로 이용해 본적이 없어서 모르겠더라구요. 하여간 깔아야할 건 드럽게 많습니다. java로 치면 Maven같은데.. 사전 준비 과정은 java보다 좀 복잡하군요.

### CocoaPods를 깔아볼까요?

1.  설치는 역시 Gem (ruby?? 인가 cocoapods가 Xcode의 경우에는 ruby로 되어 있네요... 흥미로운데 )

		$ gem install cocoapods

2. PodFile을 찾아서 아래 내용을 입력

		source 'https://github.com/CocoaPods/Specs.git'
		platform :ios, '8.0'
		use_frameworks!

		pod 'Kingfisher', '~> 1.1'

3. Command 실행

		$pod install

### Carthage도 깔아봅니다.

1. 이건 좀 간단하군요. 아니었나 봅니다.


		$ brew update
		$ brew install carthage

2. Cartfile을 찾아서 또 수정

		github "onevcat/Kingfisher" >= 1.1

3. 실행

		$ carthage update




**** 위에 방법 말고 수동도 가능해요 *****

## 정작 중요한 그래서 이건 뭔데?

 결국 이게 하는 일은 불필요한 낭비를 줄이는 목적입니다. APP을 구동할때에 보시면 image파일들에 대해서는 반복적으로 다운로드가 되는데 이 부분을 Url 기반으로 Caching을 이용해서 Download가 된다는 거죠. 즉, 메모리가 가지고 있는 Cache를 이용해서 이미지로 가지고 있고(이때 키 정보는 URL이군요), 다시 해당 URL에 다시 접근하거나 하면...가지고 있던 Cache를 뒤져서 굳이 다운로드가 없더라고 이미지를 로딩한다? 그리고 다운로드는 시작한 다운로드에 대해서는 URL이 바뀌더라도 다운이 끝까지 이뤄질 수 있는 기능을 제공하는 그러한 녀석인 것 같습니다.
  사용자에 따라서 효과는 극명할 듯 합니다. 늘 새로운 곳을 찾아다니는 USER라면 글쎄요 얼마나 큰 효과가 있을 지 모르겠지만, 자주가는 사이트가 몇 곳으로 정해져 있는 User에서는 훨씬 더 빠른 인터넷을 모바일로 즐길 수 있지 않을까 생각합니다. 게다가 모바일 환경에 Image가 점점 늘어나는 상황에서 이러한 기능이 필요해 보이긴 합니다만... 이걸 이용하지 않더라고 mobile browser기능이 점점 더 좋아지면 굳이 이걸 사용할 필요가 있을까 하는 생각이 듭니다.

##License

Kingfisher is released under the MIT license. See LICENSE for details.


<div style="text-align:right">
 Written by: 강성동(Russell.Kang)
</div>
