# UnderlineToCamel
将下滑线命名的 key 转为驼峰




```
OLD_IFS="$IFS"
IFS="_"
arr=($@)
IFS="$OLD_IFS"

i=0
for s in ${arr[@]} 
do

if [[ $i == 0 ]]; then
	let i++
	var=$s
	dst=${dst}${var}
	continue
else
	var=`echo "$s" | awk '{for (i=0;i<=NF;i++) {sub(".", substr(toupper($i), 1,1) , $i)}} {print}'`
	dst=${dst}${var}
	let i++
fi

done

echo $dst

```
