SHELL=/bin/bash
PATH:=.venv/bin:$(PATH)

ifeq ($(shell uname), Linux)
    OS:=linux
    VENV_ACTIVATE:=. .venv/bin/activate
else
    OS:=macos
    VENV_ACTIVATE:=source .venv/bin/activate
endif

GREEN:=\033[0;32m
YELLOW:=\033[0;33m
NC:=\033[0m 

install:
	@( \
		if [ ! -d .venv ]; then uv venv -p 3.12 --seed; fi; \
		$(VENV_ACTIVATE); \
		uv export --format requirements-txt --frozen --all-extras > requirements.txt ; \
		uv pip install -r requirements.txt; \
	)

lint:
	@$(VENV_ACTIVATE) && ruff check;

lint-fix:
	@$(VENV_ACTIVATE) && ruff check --fix && ruff format;