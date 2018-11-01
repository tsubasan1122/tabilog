# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


<script >
    handler = Gmaps.build('Google');
    handler.buildMap({ provider: { scrollwheel: false }, internal: {id: 'map'}}, function(){
        markers = handler.addMarkers([
            {
                "lat": <%= @trip.latitude %>,
                "lng": <%= @trip.longitude %>,
                "infowindow": '<p></p><p><%= @trip.address %></p><p><%= link_to "Googleマップで見る" ,"https://maps.google.co.jp/maps?q=loc:#{@trip.latitude},#{@trip.longitude}&iwloc=J",target: "_blank" %></p>'
            }
        ]);
        handler.bounds.extendWith(markers);
        handler.fitMapToBounds();
        handler.getMap().setZoom(17);
    });
</script>
<script>
    $(document).ready(function(){
        $('#my-slide').slick({
            // アクセシビリティ。左右ボタンで画像の切り替えをできるかどうか
            accessibility: true,
            // 自動再生。trueで自動再生される。
            autoplay: false,
            // 自動再生で切り替えをする時間
            autoplaySpeed: 3000,
            // 自動再生や左右の矢印でスライドするスピード
            speed: 400,
            // 自動再生時にスライドのエリアにマウスオンで一時停止するかどうか
            pauseOnHover: true,
            // 自動再生時にドットにマウスオンで一時停止するかどうか
            pauseOnDotsHover: true,
            // 切り替えのアニメーション。ease,linear,ease-in,ease-out,ease-in-out
            cssEase: 'ease',
            // 画像下のドット（ページ送り）を表示
            dots: false,
            // ドットのclass名をつける
            dotsClass: 'dot-class',
            // ドラッグができるかどうか
            draggable: true,
            // 切り替え時のフェードイン設定。trueでon
            fade: false,
            // 左右の次へ、前へボタンを表示するかどうか
            arrows: true,
            // 無限スクロールにするかどうか。最後の画像の次は最初の画像が表示される。
            infinite: true,
            // 最初のスライダーの位置
            initialSlide: 0,
            // 画像の遅延表示。‘ondemand’or'progressive'

            // スライドのエリアにマウスオーバーしている間、自動再生を止めるかどうか。
            pauseOnHover: true,
            // スライドのエリアに画像がいくつ表示されるかを指定
            slidesToShow: 1,
            // 一度にスライドする数
            slidesToScroll: 2,
            // タッチスワイプに対応するかどうか
            swipe: true,
            // 縦方向へのスライド
            vertical: false,
            // 表示中の画像を中央へ
            centerMode: true,
            // 中央のpadding
            centerPadding: '0px'
        });

    });
</script>
<script >
    $(function() {
        $(document).on('ajax:success', 'form', function(e) {
            console.log(e)
            $('.review__box').prepend(e.detail[2]["response"])
            $('#review_evaluation_id').val('');
            $('#review_comment').val('');
            $('#review_month').val('');
            $('#review_review_photos_attributes_0_review_image').val('');
            $('.review-registration').hide();
            $('.review__wrapper').hide();
        })
        $(document).on('click', 'input[type=submit]', function() {
            if ($('input[type=text]').val() == '') {
                return false;
            }
        })
        $(document).on('click', '.contribution', function() {
            $('.review-registration').show();
            $(".review__wrapper").show();

        })
        $(document).on("click", ".review__wrapper" , function(){
            $('.review-registration').hide();
            $('.review__wrapper').hide();
        })
    })
</script>
<script>
    $(function() {
        $(document).on("ajax:success", ".wanna", function(e) {
            if ($('#' + e.detail[0]).hasClass('heart')) {
                $('#' + e.detail[0]).removeClass('heart');
            } else {
                $('#' + e.detail[0]).addClass('heart');
            }
        })
    })
</script>

