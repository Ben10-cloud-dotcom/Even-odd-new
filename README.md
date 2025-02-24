<xml version="1.0" encoding="UTF-8"?> <dbot> <!-- Define Variables --> <variables> <variable name="even_count" type="number" value="0" /> <variable name="odd_count" type="number" value="0" /> <variable name="total_trades" type="number" value="0" /> <variable name="even_percentage" type="number" value="0" /> <variable name="odd_percentage" type="number" value="0" /> <variable name="stake_amount" type="number" value="1" /> <variable name="last_result" type="string" value="" /> </variables>

<!-- Trade Execution -->
<trade>
    <if condition="even_percentage > 55">
        <trade_type>even</trade_type>
        <stake>{{ stake_amount }}</stake>
    </if>
    <if condition="odd_percentage > 55">
        <trade_type>odd</trade_type>
        <stake>{{ stake_amount }}</stake>
    </if>
</trade>

<!-- Trade Result Handling -->
<on_trade_result>
    <set name="total_trades" value="total_trades + 1" />
    <if condition="last_result == 'even'">
        <set name="even_count" value="even_count + 1" />
    </if>
    <if condition="last_result == 'odd'">
        <set name="odd_count" value="odd_count + 1" />
    </if>
    <set name="even_percentage" value="(even_count / total_trades) * 100" />
    <set name="odd_percentage" value="(odd_count / total_trades) * 100" />
</on_trade_result>

</dbot> Even-odd-new
