I am angry.

I am very angry indeed. Besides struggling on finding relevant documentation
dealing with number formatting accross different software locales, I feel
the urge of writing. As a matter of fact, I even tried laying my own thoughts
in broken Turkish through an article entitled “Okunması gereken kitaplar”,
where I wrote about books which were worth being read.

These couple of last years, I have been building an interesting product,
starting a business eventually and, out of the blue, I had to deal with a
wide range of corner cases, where I had to parse dates, numbers, prices from
different locales. Thanksfully, as a French rooster, I am deeply interested in
my own language, mostly with its typographic rules, so I could tell you first
about them. Sometimes they are even broken by French themselves.

So I’ll start with my own mother tongue's rules, then I’ll gather rules from
as much countries / locales as possible, referring myself to them eventually
once I need them.

## Formatting numbers in French

The number separator is a *blank* or, more specifically with computers, a
[non-breaking space](https://en.wikipedia.org/wiki/Non-breaking_space). We need
to put it every three digits. Here are a few examples for your convenience:

  * 123 ;
  * 123 456 ;
  * 123 456 789 ;
  * etc.

As for the number separator, it is not the dot “.” as you would have in U.S.
English. It's the comma “,”. Yet a few more examples:

* 123,45 ;
* 123 456,78 ;
* 123 456,789 123 ;
* etc.

Note that you still have to put non-breaking spaces for the decimal part of a
decimal number.

Now, how do you express a price? First things first, the France abide by one
single currency in its territory, which is the euro (€). Contrary to the US
where you would but the dollar sign “$” in front of the price, as for the
French convention, you need to put the currency sign after the number,
separating them by yet another non-breaking space (looks like French people
like it when there's void between things, I don’t know).

So that would be:

  * 123 €
  * 123 456 €
  * 123 456,78 €
  * etc.

Note that if we are talking about US dollars, not only do we need to put "US"
after the dollar sign, but it still remains at the end of the price with
the non-breaking space. Let's bring more example for prices with different
currencies but still expressed in a French way.

  * 123,45 $US ;
  * 123,45 £ ;
  * 12 345 ¥ ;
  * etc.

What about the dates? It's `dd/mm/YYYY`, as follow: `02/10/1989` (which is
October 2nd, 1989).

How about hours? Not only do we use the 24-hour format, but we need to put
the hours, a non-breaking space, an “h”, then yet another non-breaking space
and the number of minutes. Examples:

  * 14 h 12 (2:12 pm) ;
  * 0 h 23 (12:23 am) ;
  * etc.

Putting it all together, let's imagine a simple sentence that we could
translate to highlight the different formats being used. The first one will be
in English so everytime there is a translation, you would only worry about the
format, not the sentence itself.

## Formatting numbers, worldwide.

### United States

Geoffrey spent $123.45 on 05/15/2021 at 2:12 PM.

### France

Geoffrey a dépensé 123,45 € le 15/05/2021 à 14 h 12.

## Resources

  * [Complete Wold Currency Formats](https://www.thefinancials.com/Default.aspx?SubSectionID=curformat)