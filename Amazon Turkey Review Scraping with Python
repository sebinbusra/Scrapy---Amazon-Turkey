
# Run in the terminal :
# % pip install scrapy
# % scrapy startproject scrapingproject


import scrapy
from scrapy.crawler import CrawlerProcess

class ReviewspiderSpider(scrapy.Spider):

    # Spider name
    name = 'reviewspider'

    # Domain names to scrape
    allowed_domains = ['amazon.com.tr']
    
    myBaseUrl = "https://www.amazon.com.tr/Apple-Telefon-Kulakl%C4%B1k-Adapt%C3%B6r-Garantili/product-reviews/B08PQ1JPX9/ref=cm_cr_getr_d_paging_btm_prev_2?ie=UTF8&reviewerType=all_reviews&pageNumber="
    start_urls=[]
    
    # Creating list of urls to be scraped by appending page number a the end of base url
    for i in range(1,4000):
        start_urls.append(myBaseUrl+str(i))
    # Defining a Scrapy parser
    def parse(self, response):
            data = response.css('#cm_cr-review_list')

            # Collecting product star ratings
            star_rating = data.css('.review-rating')

            # Collecting user reviews
            comments = data.css('.review-text')
            count = 0

            # Combining the results
            for review in star_rating:
                yield{'stars': ''.join(review.xpath('.//text()').extract()),
                      'comment': ''.join(comments[count].xpath(".//text()").extract())
                     }
                count=count+1

# now, run this line in the terminal to create csv data :
# scrapy runspider /Users/busrasebin/scrapingproject/scrapingproject/spiders/reviewspider.py -o 4000_scraped_data.csv
























