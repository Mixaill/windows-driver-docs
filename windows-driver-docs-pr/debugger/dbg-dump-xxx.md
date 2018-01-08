---
title: DBG\_DUMP\_XXX
description: DBG\_DUMP\_XXX
ms.assetid: d34ecf95-3aea-4850-a2de-76f239e8b8a0
ms.author: windowsdriverdev
ms.date: 12/07/2017
ms.topic: article
ms.prod: windows-hardware
ms.technology: windows-devices
keywords: ["DBG_DUMP_XXX Windows Debugging"]
topic_type:
- apiref
api_name:
- DBG_DUMP_XXX
api_location:
- wdbgexts.h
api_type:
- HeaderDef
---

# DBG\_DUMP\_XXX


## <span id="ddk_dbg_dump_xxx_dbx"></span><span id="DDK_DBG_DUMP_XXX_DBX"></span>


The DBG\_DUMP\_*XXX* bit flags are used by the **Options** member of the SYM\_DUMP\_PARAM structure to control the behavior of the [**IG\_DUMP\_SYMBOL\_INFO**](https://msdn.microsoft.com/library/windows/hardware/ff550906)[**Ioctl**](https://msdn.microsoft.com/library/windows/hardware/ff551084) operation.

The following flags can be present.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Flag</th>
<th align="left">Effect</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>DBG_DUMP_NO_INDENT</p></td>
<td align="left"><p>Members are not indented in the output.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DBG_DUMP_NO_OFFSET</p></td>
<td align="left"><p>Offsets are not printed.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DBG_DUMP_VERBOSE</p></td>
<td align="left"><p>Verbose output.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DBG_DUMP_CALL_FOR_EACH</p></td>
<td align="left"><p>A callback function is called for each member.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DBG_DUMP_LIST</p></td>
<td align="left"><p>The symbol is an entry in a linked list and the IG_DUMP_SYMBOL_INFO <strong>Ioctl</strong> operation will iterate over this list. The description of the member that points to the next item in the list is specified by the <strong>linkList</strong> member of the SYM_DUMP_PARAM structure.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DBG_DUMP_NO_PRINT</p></td>
<td align="left"><p>Nothing is printed (only callback functions are called and data copies are performed).</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DBG_DUMP_GET_SIZE_ONLY</p></td>
<td align="left"><p>The <strong>Ioctl</strong> operation returns the size of the symbol only; it will not print member information or call callback functions.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DBG_DUMP_COMPACT_OUT</p></td>
<td align="left"><p>Newlines are not printed after each member.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DBG_DUMP_ARRAY</p></td>
<td align="left"><p>The symbol is an array. The number of elements in the array is specified by the member <strong>listLink-&gt;size</strong> of the SYM_DUMP_PARAM structure.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DBG_DUMP_ADDRESS_OF_FIELD</p></td>
<td align="left"><p>The value of <strong>addr</strong> is actually the address of the member <strong>listLink-&gt;fName</strong> of the SYM_DUMP_PARAM structure and not the beginning of the symbol.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DBG_DUMP_ADDRESS_AT_END</p></td>
<td align="left"><p>The value of <strong>addr</strong> is actually the address at the end of the symbol and not the beginning of the symbol.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DBG_DUMP_COPY_TYPE_DATA</p></td>
<td align="left"><p>The value of the symbol is copied into the member <strong>pBuffer</strong>. This can only be used for primitive types--for example, ULONG or PVOID--it cannot be used with structures.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DBG_DUMP_READ_PHYSICAL</p></td>
<td align="left"><p>The symbol's value will be read directly from the target's physical memory.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DBG_DUMP_FUNCTION_FORMAT</p></td>
<td align="left"><p>When formatting a symbol that has a function type, the function format will be used, for example, <code>function(arg1, arg2, ...)</code></p></td>
</tr>
<tr class="odd">
<td align="left"><p>DBG_DUMP_BLOCK_RECURSE</p></td>
<td align="left"><p>Recurse through nested structures; but do not follow pointers.</p></td>
</tr>
</tbody>
</table>

 

In addition, the result of the macro DBG\_DUMP\_RECUR\_LEVEL(*Level*) can be added to the bit-set to specify how deep into structures to recurse. *Level* can be a number between 0 and 15.

Requirements
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">Wdbgexts.h (include Wdbgexts.h, Wdbgexts.h, or Dbgeng.h)</td>
</tr>
</tbody>
</table>

## <span id="see_also"></span>See also


[**IG\_DUMP\_SYMBOL\_INFO**](https://msdn.microsoft.com/library/windows/hardware/ff550906)

[**Ioctl**](https://msdn.microsoft.com/library/windows/hardware/ff551084)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[debugger\debugger]:%20DBG_DUMP_XXX%20%20RELEASE:%20%2811/30/2017%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




