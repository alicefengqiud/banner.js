# banner.js
banner

function carousel(){
    var number=$(".banner ul li").size()-1;//
    var cur=0;//
    var timer=0;//

    //
    function slideNext(){
        if(cur<number){
            $(".banner ul li").eq(cur).stop().fadeOut();
            $(".banner ul li").eq(cur+1).stop().fadeIn();
            $(".indicator a").removeClass().eq(cur+1).addClass("cur");
            cur+=1;
        }else{
            $(".banner ul li").eq(cur).stop().fadeOut();
            $(".banner ul li").eq(0).stop().fadeIn();
            $(".indicator a").removeClass().eq(0).addClass("cur");
            cur=0;
        }
    }
    //
    function slidePrev(){
        if(cur>0){
            $(".banner ul li").eq(cur).stop().fadeOut();
            $(".banner ul li").eq(cur-1).stop().fadeIn();
            $(".indicator a").removeClass().eq(cur-1).addClass("cur");
            cur-=1;
        }else{
            $(".banner ul li").eq(cur).stop().fadeOut();
            $(".banner ul li").eq(number).stop().fadeIn();
            $(".indicator a").removeClass().eq(number).addClass("cur");
            cur=number;
        }
    }

    timer=setInterval(slideNext,3000);

    //
    $(".banner").mouseover(function(){
        clearInterval(timer);
    });
    $(".banner").mouseout(function(){
        timer=setInterval(slideNext,3000)
    });

    //
    $(".banner .prev").click(function(){
        slidePrev();
    });
    $(".banner .next").click(function(){
        slideNext();
    });

    //
    $(".indicator>a").mouseover(function(){
        var now=$(this).index();//
        $(".indicator>a").removeClass();//
        $(this).addClass("cur");//Ϊ
        $(".banner ul li").eq(cur).fadeOut();//
        $(".banner ul li").eq(now).stop().fadeIn();//
        cur=now;//
    });
}
