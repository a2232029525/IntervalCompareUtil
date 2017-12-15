package com.yanchuan.yanchuanjiaoyu.util;

/**
 * Created by 22320 on 2017/8/24.
 */

public class IntervalUtil {
    /**
     *
     * @param str 区间字符串
     * @param value 要比较的值
     */
    public static boolean compare(String str,double value){
        StringBuffer buffer = new StringBuffer();
        String replace = null;
        if(str.startsWith("<")){
            replace = str.replace("<", "[");
        }else {
            replace=str;
        }
        buffer.append(replace);
        int center = buffer.indexOf(",");
        String oneMath = buffer.substring(1, center);
        double oneDouble = Double.parseDouble(oneMath);

        String twoMath=buffer.substring(center+1,replace.length()-1);
        double twoDouble=Double.parseDouble(twoMath);
        if(replace.startsWith("(")){
            if(oneDouble >=value){
                return false;
            }
        }

        if(replace.startsWith("[")){
            if(oneDouble >value){
                return false;
            }
        }

        if(replace.endsWith(")")){
            if(twoDouble<=value){
                return false;
            }
        }

        if(replace.endsWith("]")){
            if(twoDouble<value){
                return false;
            }
        }
        return true;
    }

    public static int getIndex(int a){

        if(compare("[0,1]",a)){
            return 0;
        }
        if(compare("[2,3]",a)){
            return 1;
        }
        if(compare("[4,5]",a)){
            return 2;
        }
        if(compare("[6,7]",a)){
            return 3;
        }
        if(compare("[8,9]",a)){
            return 4;
        }
        return 0;
    }
}

